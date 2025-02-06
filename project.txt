import streamlit as st

def get_coffee_recommendation():

    st.title("Brew Buddy : Your Friendly Coffee Companion")
    st.header("☕ Coffee Bot: Your Personalized Coffee Assistant")
    st.subheader("Get the perfect coffee based on your preferences!")

    user_name = st.text_input("Enter Your Name")

    if user_name:
        st.write(f"Welcome, {user_name}!")

    user_contactno = st.text_input("Enter Your Contact Number")

    if user_contactno and user_contactno.isdigit() and len(user_contactno) == 10:
        st.success("Valid Contact Number")
    elif user_contactno:
        st.error("Invalid Contact Number")

    user_input = st.selectbox("How would you like to proceed?",
                              ["Order Coffee", "Ask for Menu", "Exit"])

    if user_input == "Order Coffee":
        coffee_type = st.selectbox("What type of Coffee do you want?",
                                   ["Espresso", "Americano", "Latte", "Cappuccino", "Mocha",
                                    "Iced Coffee", "Iced Latte", "Frappuccino", "Turkish Coffee", "Cold brew"])

        coffee_size = st.selectbox("What Size do you want?", ["Small", "Medium", "Large"])

        coffee_strength = st.selectbox("Select the strength of your Coffee",
                                       ["Little Roast", "Medium Roast", "Dark Roast", "Extra Strong",
                                        "Regular Strong", "Mild Strength"])

        sugar_option = st.selectbox("Select a Sugar option",
                                    ["White Sugar", "Brown Sugar", "Raw Sugar", "Honey",
                                     "Maple Syrup", "Coconut Syrup", "Artificial Sweeteners"])

        confirm_order = st.button("Confirm Order")
        if confirm_order:
            st.success(
                f"Hey {user_name} Your {coffee_type} with {coffee_size} size, {coffee_strength} strength, and {sugar_option} has been confirmed!")
        else:
            st.warning("Your order is not confirmed yet.")

    elif user_input == "Ask for Menu":
        st.write("Our menu includes:")
        menu_items = ["Espresso", "Americano", "Latte", "Cappuccino", "Mocha",
                      "Iced Coffee", "Iced Latte", "Frappuccino", "Turkish Coffee", "Cold brew"]
        for item in menu_items:
            st.write(f"- {item}")

        st.write("You can now order your coffee!")

        coffee_type = st.selectbox("What type of Coffee do you want?", menu_items)

        coffee_size = st.selectbox("What Size do you want?", ["Small", "Medium", "Large"])

        coffee_strength = st.selectbox("Select the strength of your Coffee",
                                       ["Little Roast", "Medium Roast", "Dark Roast", "Extra Strong",
                                        "Regular Strong", "Mild Strength"])

        sugar_option = st.selectbox("Select a Sugar option",
                                    ["White Sugar", "Brown Sugar", "Raw Sugar", "Honey",
                                     "Maple Syrup", "Coconut Syrup", "Artificial Sweeteners"])

        confirm_order = st.button("Confirm Order")
        if confirm_order:
            st.success(
                f"Hey {user_name} Your {coffee_type} with {coffee_size} size, {coffee_strength} strength, and {sugar_option} has been confirmed!")

        else:
            st.warning("Your order is not confirmed yet.")


    elif user_input == "Exit":
        st.write("Thank you for visiting! Please come again.")

# Call the function to run the app
get_coffee_recommendation()
