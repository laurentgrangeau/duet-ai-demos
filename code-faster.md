I am new to Google Cloud and I want to use the Cloud Code extension.
Give me some examples of Google services that I can use to build and deploy a
sample app using containers.

What is the difference between Cloud Run and Cloud Functions? Explain to me
in simple terms as I am new to Google Cloud.

How to create a new Cloud Run app in Cloud Code using the command palette?
What languages are supported?

Explain Dockerfile

What is the function of the app.py file in Dockerfile?

What is the function of `K_SERVICE` and `K_REVISION` in the `app.py` file?

Explain
    service = os.environ.get('K_SERVICE', 'Unknown service')
    revision = os.environ.get('K_REVISION', 'Unknown revision')

New file inventory.py

Create a variable called inventory which is a list of 3 JSON objects.
Each JSON object has 2 attributes: productid and onhandqty.
Both attributes are strings.

Import inventory
from inventory import inventory

# Generate an App route to display a list of inventory
# items in the JSON format from the
# inventory.py file. Use the GET method.
@app.route('/inventory', methods=['GET'])
def get_inventory():
    """Return a list of inventory items."""
    return jsonify(inventory)

from flask import Flask, render_template, jsonify

# Generate an App route to get an inventory item
# given the productid. Use the GET method.
# If there is an invalid productid,
# display a 404 error.
@app.route('/inventory/<productid>', methods=['GET'])
def get_inventory_item(productid):
    """Return an inventory item given the productid."""
    for item in inventory:
        if item["productid"] == productid:
           return jsonify(item)
    return jsonify({"error": "Item not found"}), 404

How do I run a Cloud Run app locally within Cloud Code?
Is there an emulator?

Go to
http://localhost:8080/
http://localhost:8080/inventory
http://localhost:8080/inventory/1234567890

Deploy to Cloud Run.