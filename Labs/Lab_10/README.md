# Lab 10

<img width="469" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/143e76e1-12a7-4057-9198-4f3d9a43e47d">

<img width="469" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/464e6a6f-f03a-4487-be09-cee238192710">

<img width="464" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/39081d1c-e1e1-4af3-bb9c-6469b0d9fe7f">

<img width="469" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/bce52214-f2df-4920-b355-4905260ba3b9">

<img width="465" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/1f144779-3261-4e38-a92b-c168ead1a583">

(myenv) johnmfb@iLaptop:/mnt/c/Users/jjjay/OneDrive - stevens.edu/Semester 5 Courses/CPE 322/CPE-322/Labs/Lab_10/lesson10$ cat snakecoin-server-full-code.py 
# Gerald Nash, "Let’s Make the Tiniest Blockchain Bigger Part 2: With More Lines of Python"
# Referred to https://www.pythonanywhere.com/forums/topic/12382/ that fixed sha.update() TypeError: Unicode-objects must be encoded before hashing
# Running on http://127.0.0.1:5000/mine (Reload the page to mine and press CTRL+C to quit)
from flask import Flask
from flask import request
import json
import requests
import hashlib as hasher
import datetime as date
from flask import send_from_directory
import os
node = Flask(__name__)

# Define what a Snakecoin block is
class Block:
  def __init__(self, index, timestamp, data, previous_hash):
    self.index = index
    self.timestamp = timestamp
    self.data = data
    self.previous_hash = previous_hash
    self.hash = self.hash_block()
  
  def hash_block(self):
    sha = hasher.sha256()
#    sha.update(str(self.index) + str(self.timestamp) + str(self.data) + str(self.previous_hash))
    sha.update((str(self.index) + str(self.timestamp) + str(self.data) + str(self.previous_hash)).encode("utf-8"))
    return sha.hexdigest()

# Generate genesis block
def create_genesis_block():
  # Manually construct a block with
  # index zero and arbitrary previous hash
  return Block(0, date.datetime.now(), {
    "proof-of-work": 9,
    "transactions": None
  }, "0")

# A completely random address of the owner of this node
miner_address = "q3nf394hjg-random-miner-address-34nf3i4nflkn3oi"
# This node's blockchain copy
blockchain = []
blockchain.append(create_genesis_block())
# Store the transactions that
# this node has in a list
this_nodes_transactions = []
# Store the url data of every
# other node in the network
# so that we can communicate
# with them
peer_nodes = []
# A variable to deciding if we're mining or not
mining = True

@node.route("/")
def hello():
    return "SnakeCoin Server"

@node.route('/favicon.ico')
def favicon():
    return send_from_directory(os.path.join(node.root_path, 'static'),
                               'favicon.ico',
                               mimetype='image/vnd.microsoft.icon')

@node.route('/txion', methods=['POST'])
def transaction():
  # On each new POST request,
  # we extract the transaction data
  new_txion = request.get_json()
  # Then we add the transaction to our list
  this_nodes_transactions.append(new_txion)
  # Because the transaction was successfully
  # submitted, we log it to our console
  print("New transaction")
  print(("FROM: {}".format(new_txion['from'].encode('ascii','replace'))))
  print(("TO: {}".format(new_txion['to'].encode('ascii','replace'))))
  print(("AMOUNT: {}\n".format(new_txion['amount'])))
  # Then we let the client know it worked out
  return "Transaction submission successful\n"

@node.route('/blocks', methods=['GET'])
def get_blocks():
  chain_to_send = blockchain
  # Convert our blocks into dictionaries
  # so we can send them as json objects later
  for i in range(len(chain_to_send)):
    block = chain_to_send[i]
    block_index = str(block.index)
    block_timestamp = str(block.timestamp)
    block_data = str(block.data)
    block_hash = block.hash
    chain_to_send[i] = {
      "index": block_index,
      "timestamp": block_timestamp,
      "data": block_data,
      "hash": block_hash
    }
  chain_to_send = json.dumps(chain_to_send)
  return chain_to_send

def find_new_chains():
  # Get the blockchains of every
  # other node
  other_chains = []
  for node_url in peer_nodes:
    # Get their chains using a GET request
    block = requests.get(node_url + "/blocks").content
    # Convert the JSON object to a Python dictionary
    block = json.loads(block)
    # Add it to our list
    other_chains.append(block)
  return other_chains

def consensus():
  # Get the blocks from other nodes
  other_chains = find_new_chains()
  # If our chain isn't longest,
  # then we store the longest chain
  longest_chain = blockchain
  for chain in other_chains:
    if len(longest_chain) < len(chain):
      longest_chain = chain
  # If the longest chain isn't ours,
  # then we stop mining and set
  # our chain to the longest one
  blockchain = longest_chain

def proof_of_work(last_proof):
  # Create a variable that we will use to find
  # our next proof of work
  incrementor = last_proof + 1
  # Keep incrementing the incrementor until
  # it's equal to a number divisible by 9
  # and the proof of work of the previous
  # block in the chain
  while not (incrementor % 9 == 0 and incrementor % last_proof == 0):
    incrementor += 1
  # Once that number is found,
  # we can return it as a proof
  # of our work
  return incrementor

@node.route('/mine', methods = ['GET'])
def mine():
  # Get the last proof of work
  last_block = blockchain[len(blockchain) - 1]
  last_proof = last_block.data['proof-of-work']
  # Find the proof of work for
  # the current block being mined
  # Note: The program will hang here until a new
  #       proof of work is found
  proof = proof_of_work(last_proof)
  # Once we find a valid proof of work,
  # we know we can mine a block so
  # we reward the miner by adding a transaction
  this_nodes_transactions.append(
    { "from": "network", "to": miner_address, "amount": 1 }
  )
  # Now we can gather the data needed
  # to create the new block
  new_block_data = {
    "proof-of-work": proof,
    "transactions": list(this_nodes_transactions)
  }
  new_block_index = last_block.index + 1
  new_block_timestamp = this_timestamp = date.datetime.now()
  last_block_hash = last_block.hash
  # Empty transaction list
  this_nodes_transactions[:] = []
  # Now create the
  # new block!
  mined_block = Block(
    new_block_index,
    new_block_timestamp,
    new_block_data,
    last_block_hash
  )
  blockchain.append(mined_block)
  # Let the client know we mined a block
  return json.dumps({
      "index": new_block_index,
      "timestamp": str(new_block_timestamp),
      "data": new_block_data,
      "hash": last_block_hash
  }) + "\n"

node.run()

# Mining

<img width="591" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/c2c43765-b5a2-42b7-aada-7842c410f383">

<img width="1231" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/9d81974c-506f-42cf-ae12-fc214f45830a">

<img width="608" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/a65a3f05-55be-47f4-bf86-20633ba0f640">

## Git clone app and uncomment last line node_server.py

<img width="610" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/a6c96e69-04e7-48a3-a6cf-7c6d61b67e4d">


<img width="627" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/f7c9f79c-17c8-4ef6-8974-4a427fb878ee">

<img width="471" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/f44f8cf3-1dd4-4200-bf1f-2e372074b3a1">

<img width="1243" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/3243ffb9-5619-44ed-bf5d-3b8704a2e5a4">

<img width="605" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/4c740c54-601b-467f-93cd-cc698bab9b8f">

<img width="603" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/e9e99267-7a27-4614-987a-6a56601b666f">

## Have a great break!

![Alt Text]([URL_of_the_GIF](https://www.google.com/url?sa=i&url=https%3A%2F%2Fjustmaths.co.uk%2F2016%2F10%2F25%2Fcouldnt-let-it-pass-by-without%2Fcelebration-gif%2F&psig=AOvVaw0VAjLd4g__3pnu3sTQamv-&ust=1702937341099000&source=images&cd=vfe&ved=0CBEQjRxqFwoTCPD2qou-l4MDFQAAAAAdAAAAABAE)https://www.google.com/url?sa=i&url=https%3A%2F%2Fjustmaths.co.uk%2F2016%2F10%2F25%2Fcouldnt-let-it-pass-by-without%2Fcelebration-gif%2F&psig=AOvVaw0VAjLd4g__3pnu3sTQamv-&ust=1702937341099000&source=images&cd=vfe&ved=0CBEQjRxqFwoTCPD2qou-l4MDFQAAAAAdAAAAABAE)
