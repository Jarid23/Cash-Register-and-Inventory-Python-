# Cash-Register-and-Inventory-Python-

#Python program that operates a menu and an inventory with user input. 

import retail_item
import cash_register

SHOW = 1
PURCHASE = 2
TOTAL = 3
EMPTY = 4
QUIT = 5

def main():
    # Set all variables to zero
    lister = []
    inv=[]
    cost=[]
    desc=''
    inventory=0
    price=0
    total=0
    purchase=0
    # Set variable for each class
    cash=cash_register.CashRegister(purchase, total, lister, inv, cost)
    retail=retail_item.RetailItem(desc, inventory, price)

    desc = 'Jacket'
    inventory = 12
    price = 59.95
    # Setting classes
    retail.set_desc(desc)
    retail.set_inventory(inventory)
    retail.set_price(price)
    # Adding to cart
    cash.purchase_item(retail.get_desc(), lister)
    cash.purchase_item(retail.get_inventory(), inv)
    cash.purchase_item(retail.get_price(), cost)

    desc = 'Jeans'
    inventory = 40
    price = 34.95
    retail.set_desc(desc)
    retail.set_inventory(inventory)
    retail.set_price(price)
    cash.purchase_item(retail.get_desc(), lister)
    cash.purchase_item(retail.get_inventory(), inv)
    cash.purchase_item(retail.get_price(), cost)

    desc = 'Shirt'
    inventory = 20
    price = 24.95
    retail.set_desc(desc)
    retail.set_inventory(inventory)
    retail.set_price(price)
    cash.purchase_item(retail.get_desc(), lister)
    cash.purchase_item(retail.get_inventory(), inv)
    cash.purchase_item(retail.get_price(), cost)

    choice = 0

    # Process menu selections until user quits program.
    while choice != QUIT:
        # Get the user's menu choice.
        choice = get_menu_choice()
        # Proces the choice.
        if choice == SHOW:
            show_items(cash, retail, lister, inv, cost)
        elif choice == PURCHASE:
            purchase_item(cash, retail, lister, inv, cost)
        elif choice == TOTAL:
            get_total(cash, retail, lister)
        elif choice == EMPTY:
            price=0
            cash.set_total(price)
            clear(cash, lister)

# The get_menu_choice function displays the menu and gets
# a validated choice from the user.
def get_menu_choice():
    print()
    print('CASH REGISTER MENU')
    print('-------------------------')
    print('1) Show Inventory')
    print('2) Purchase Item(s)')
    print('3) Show Total of Items Purchased')
    print('4) Empty Shopping Cart')
    print('5) Quit')
    print()

    # Get the user's choice.
    choice = int(input('Enter a choice: '))

    # Validate the choice.
    while choice < SHOW or choice > QUIT:
        choice = int(input('Please enter a valid choice: '))

    # Return the user's choice.
    return choice

def show_items(cash, retail, lister, inv, cost):
    print('\t\tDescription\t\tUnits in Inventory\t\tPrice')
    print('--------------------------------------------------------------------------------')
    cash.show_item(lister, inv, cost)

def purchase_item(cash, retail, lister, inv, cost):
# menu using global constants
    JACKET=1
    JEANS=2
    SHIRT=3
    QUIT=4
    choice=0

    print()
    print('WHICH WOULD YOU LIKE TO BUY')
    print('-------------------------')
    print('1) Jacket')
    print('2) Jeans')
    print('3) Shirt')
    print('4) Quit')
    print()

    print('Choose as many as you like. Press 4 then ENTER to quit.')
    while choice != QUIT:
        # Get the user's menu choice.
        choice = int(input('Which would you like to buy: '))
        if choice < JACKET or choice > QUIT:
            choice = int(input('Please enter a valid choice: '))

        while choice != QUIT:
            # Proces the choice.
            if choice == JACKET:
                desc = 'Jacket'
                inventory = 12
                price = 59.95
                retail.set_desc(desc)
                retail.set_inventory(inventory)
                retail.set_price(price)
                cash.purchase_item(retail.get_desc(), lister)
                cash.purchase_item(retail.get_inventory(), inv)
                cash.purchase_item(retail.get_price(), cost)
                cash.set_total(price)
                break
            elif choice == JEANS:
                desc = 'Jeans'
                inventory = 40
                price = 34.95
                retail.set_desc(desc)
                retail.set_inventory(inventory)
                retail.set_price(price)
                cash.purchase_item(retail.get_desc(), lister)
                cash.purchase_item(retail.get_inventory(), inv)
                cash.purchase_item(retail.get_price(), cost)
                cash.set_total(price)
                break
            elif choice == SHIRT:
                desc = 'Shirt'
                inventory = 20
                price = 24.95
                retail.set_desc(desc)
                retail.set_inventory(inventory)
                retail.set_price(price)
                cash.purchase_item(retail.get_desc(), lister)
                cash.purchase_item(retail.get_inventory(), inv)
                cash.purchase_item(retail.get_price(), cost)
                cash.set_total(price)
                break
    print()

def get_total(cash, retail, lister):
    print()
    cash.show_items(cash.get_list(lister))
    print('Your total is: $', format(cash.cost_total(),',.2f'))

def clear(cash, lister):
    print('Shopping cart emptied.')
    lister=lister.clear()
    price=0
    cash.set_total(price)

    return lister
# Call the main function
main()
