# Shopping-Cart
## Set-up Instructions
Welcome to the Shopping Cart Exercise! To start, create a new remote project repository in Github called "shopping-cart". When creating the repo, make sure to add a "README.md" file and a Python-flavored ".gitignore" file. After this process is complete, you should be able to view the repo on GitHub at an address like https://github.com/YOUR_USERNAME/shopping-cart.

After creating the remote repo, use GitHub Desktop software or the command-line to "clone" it onto your computer. Choose the Desktop location to store the repo.

After cloning the repo, navigate there from the command-line:
```
cd ~/Desktop/shopping-cart 
```
Next, use your text editor to create a new file called "shopping_cart.py" and enter the following:
```
# shopping_cart.py

products = [
    {"id":1, "name": "Chocolate Sandwich Cookies", "department": "snacks", "aisle": "cookies cakes", "price": 3.50},
    {"id":2, "name": "All-Seasons Salt", "department": "pantry", "aisle": "spices seasonings", "price": 4.99},
    {"id":3, "name": "Robust Golden Unsweetened Oolong Tea", "department": "beverages", "aisle": "tea", "price": 2.49},
    {"id":4, "name": "Smart Ones Classic Favorites Mini Rigatoni With Vodka Cream Sauce", "department": "frozen", "aisle": "frozen meals", "price": 6.99},
    {"id":5, "name": "Green Chile Anytime Sauce", "department": "pantry", "aisle": "marinades meat preparation", "price": 7.99},
    {"id":6, "name": "Dry Nose Oil", "department": "personal care", "aisle": "cold flu allergy", "price": 21.99},
    {"id":7, "name": "Pure Coconut Water With Orange", "department": "beverages", "aisle": "juice nectars", "price": 3.50},
    {"id":8, "name": "Cut Russet Potatoes Steam N' Mash", "department": "frozen", "aisle": "frozen produce", "price": 4.25},
    {"id":9, "name": "Light Strawberry Blueberry Yogurt", "department": "dairy eggs", "aisle": "yogurt", "price": 6.50},
    {"id":10, "name": "Sparkling Orange Juice & Prickly Pear Beverage", "department": "beverages", "aisle": "water seltzer sparkling water", "price": 2.99},
    {"id":11, "name": "Peach Mango Juice", "department": "beverages", "aisle": "refrigerated", "price": 1.99},
    {"id":12, "name": "Chocolate Fudge Layer Cake", "department": "frozen", "aisle": "frozen dessert", "price": 18.50},
    {"id":13, "name": "Saline Nasal Mist", "department": "personal care", "aisle": "cold flu allergy", "price": 16.00},
    {"id":14, "name": "Fresh Scent Dishwasher Cleaner", "department": "household", "aisle": "dish detergents", "price": 4.99},
    {"id":15, "name": "Overnight Diapers Size 6", "department": "babies", "aisle": "diapers wipes", "price": 25.50},
    {"id":16, "name": "Mint Chocolate Flavored Syrup", "department": "snacks", "aisle": "ice cream toppings", "price": 4.50},
    {"id":17, "name": "Rendered Duck Fat", "department": "meat seafood", "aisle": "poultry counter", "price": 9.99},
    {"id":18, "name": "Pizza for One Suprema Frozen Pizza", "department": "frozen", "aisle": "frozen pizza", "price": 12.50},
    {"id":19, "name": "Gluten Free Quinoa Three Cheese & Mushroom Blend", "department": "dry goods pasta", "aisle": "grains rice dried goods", "price": 3.99},
    {"id":20, "name": "Pomegranate Cranberry & Aloe Vera Enrich Drink", "department": "beverages", "aisle": "juice nectars", "price": 4.25}
] # based on data from Instacart: https://www.instacart.com/datasets/grocery-shopping-2017


def to_usd(my_price):
    """
    Converts a numeric value to usd-formatted string, for printing and display purposes.

    Param: my_price (int or float) like 4000.444444

    Example: to_usd(4000.444444)

    Returns: $4,000.44
    """
    return f"${my_price:,.2f}" #> $12,000.71


# TODO: write some Python code here to produce the desired output

print(products)
```
At this point make sure to save your work.

### Further Set-up
If you choose to tackle bonus challenges, third-pary packages will be required.  Enter the below in your command line, if so:
```
# IF USING THIRD-PARTY PACKAGES, USE A NEW ENV:
conda create -n shopping-env python=3.8 
```

```
conda activate shopping-env
```

```
pip install -r requirements.txt # (after specifying desired packages inside)
```

Finally,  in your command line enter the below to run the Python script. If you see the provided "products" data structure, you're ready to move on to project development. 
```
python shopping_cart.py
```

### Helpful Tool
For further assistance in setting up and later developing this project, please see the **below** link to a guided screencast.
[Guided Screencast](https://www.youtube.com/watch?v=3BaGb-1cIr0&feature=youtu.be)

## Development and Usage
### Basic Requirements
In order to run this project, you will need to have an understanding of the following functions, statements, modules, and datatypes:
1. input function
2. if/else/break
3. Datetime
4. For loops
5. list datatype
6. to_usd function

An example of the expected desired output should look something like this:
> ----------
>
> Rich's Groceries
>
> www.Richsgroceries.com
> 
> ----------
>
> Checkout at: 2022-07-28 11:32:57
>
> ----------
>
> Selected Product: All-Seasons Salt  $4.99
>
> Selected Product: Robust Golden Unsweetened Oolong Tea  $2.49
>
> ----------
>
> Subtotal Price: $7.49
>
> Tax: $0.65
>
> Total Price: $8.13
>
> ----------
>
> Thanks for shopping, see you soon!

## Further Exploration
### Sending an email to yourself
In order to approach this further exploration challenge, you will need to follow these steps:

#### Installation
From within an active virtual environment, install the sendgrid package:
```
pip install sendgrid
```

#### Setup
Next,  sign up for a SendGrid account [SendGrid](app.sendgrid.com), then follow the instructions to complete your "Single Sender Verification", clicking the link in a confirmation email to verify your account. 

Create a SendGrid API Key with "full access" permissions and store your API Key value in an environment variable called "SENDGRID_API_KEY".

Also set an environment variable called "SENDER_ADDRESS" to be the same email address as the single sender address you associated with your SendGrid account.

Finally, use a ".env" file to manage these environment variables.

#### Usage
Send yourself an email using the below structure code.  Make sure to edit the subject and html_content as it pertains to your desired output. If you see a status code of 202, it means the message was sent successfully.

```
import os
from dotenv import load_dotenv
from sendgrid import SendGridAPIClient
from sendgrid.helpers.mail import Mail

load_dotenv()

SENDGRID_API_KEY = os.getenv("SENDGRID_API_KEY", default="OOPS, please set env var called 'SENDGRID_API_KEY'")
SENDER_ADDRESS = os.getenv("SENDER_ADDRESS", default="OOPS, please set env var called 'SENDER_ADDRESS'")

client = SendGridAPIClient(SENDGRID_API_KEY) #> <class 'sendgrid.sendgrid.SendGridAPIClient>
print("CLIENT:", type(client))

subject = "Your Receipt from the Green Grocery Store"

html_content = "Hello World"
print("HTML:", html_content)

# FYI: we'll need to use our verified SENDER_ADDRESS as the `from_email` param
# ... but we can customize the `to_emails` param to send to other addresses
message = Mail(from_email=SENDER_ADDRESS, to_emails=SENDER_ADDRESS, subject=subject, html_content=html_content)

try:
    response = client.send(message)

    print("RESPONSE:", type(response)) #> <class 'python_http_client.client.Response'>
    print(response.status_code) #> 202 indicates SUCCESS
    print(response.body)
    print(response.headers)

except Exception as err:
    print(type(err))
    print(err)
```
Finally check your inbox to see the email.