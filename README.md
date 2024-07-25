public class InventoryItem
{
    // Properties
    public string ItemName { get; set; }
    public int ItemId { get; set; }
    public double Price { get; set; }
    public int QuantityInStock { get; set; }

    // Constructor
    public InventoryItem(string itemName, int itemId, double price, int quantityInStock)
    {
        // TODO: Initialize the properties with the values passed to the constructor.
    }

    // Methods

    // Update the price of the item
    public void UpdatePrice(double newPrice)
    {
        // TODO: Update the item's price with the new price.
    }

    // Restock the item
    public void RestockItem(int additionalQuantity)
    {
        // TODO: Increase the item's stock quantity by the additional quantity.
    }

    // Sell an item
    public void SellItem(int quantitySold)
    {
        // TODO: Decrease the item's stock quantity by the quantity sold.
        // Make sure the stock doesn't go negative.
    }

    // Check if an item is in stock
    public bool IsInStock()
    {
        // TODO: Return true if the item is in stock (quantity > 0), otherwise false.
    }

    // Print item details
    public void PrintDetails()
    {
        // TODO: Print the details of the item (name, id, price, and stock quantity).
    }
}
class Program
{
    static void Main(string[] args)
    {
        // Creating instances of InventoryItem
        InventoryItem item1 = new InventoryItem("Laptop", 101, 1200.50, 10);
        InventoryItem item2 = new InventoryItem("Smartphone", 102, 800.30, 15);

        // TODO: Implement logic to interact with these objects.
        // Example tasks:
        // 1. Print details of all items.
        // 2. Sell some items and then print the updated details.
        // 3. Restock an item and print the updated details.
        // 4. Check if an item is in stock and print a message accordingly.


    }
}



using System;

public class InventoryItem
{
    // Properties
    public string ItemName { get; set; }
    public int ItemId { get; set; }
    public double Price { get; set; }
    public int QuantityInStock { get; set; }

    // Constructor
    public InventoryItem(string itemName, int itemId, double price, int quantityInStock)
    {
        ItemName = itemName;
        ItemId = itemId;
        Price = price;
        QuantityInStock = quantityInStock;
    }

    // Methods

    // Update the price of the item
    public void UpdatePrice(double newPrice)
    {
        Price = newPrice;
        Console.WriteLine($"Price of {ItemName} updated to {Price:C}");
    }

    // Restock the item
    public void RestockItem(int additionalQuantity)
    {
        QuantityInStock += additionalQuantity;
        Console.WriteLine($"{additionalQuantity} {ItemName}(s) added to stock. New stock: {QuantityInStock}");
    }

    // Sell an item
    public void SellItem(int quantitySold)
    {
        if (quantitySold <= QuantityInStock)
        {
            QuantityInStock -= quantitySold;
            Console.WriteLine($"{quantitySold} {ItemName}(s) sold. Remaining stock: {QuantityInStock}");
        }
        else
        {
            Console.WriteLine($"Not enough stock to sell {quantitySold} {ItemName}(s).");
        }
    }

    // Check if an item is in stock
    public bool IsInStock()
    {
        return QuantityInStock > 0;
    }

    // Print item details
    public void PrintDetails()
    {
        Console.WriteLine($"Item: {ItemName} (ID: {ItemId})");
        Console.WriteLine($"Price: {Price:C}");
        Console.WriteLine($"Quantity in stock: {QuantityInStock}");
        Console.WriteLine();
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Creating instances of InventoryItem
        InventoryItem item1 = new InventoryItem("Laptop", 101, 1200.50, 10);
        InventoryItem item2 = new InventoryItem("Smartphone", 102, 800.30, 15);

        // Display initial inventory details
        Console.WriteLine("Initial Inventory Details:");
        item1.PrintDetails();
        item2.PrintDetails();

        // Menu-driven interaction with the inventory items
        bool exit = false;
        while (!exit)
        {
            Console.WriteLine("Choose an option:");
            Console.WriteLine("1. Print inventory details");
            Console.WriteLine("2. Sell an item");
            Console.WriteLine("3. Restock an item");
            Console.WriteLine("4. Update price of an item");
            Console.WriteLine("5. Check if an item is in stock");
            Console.WriteLine("6. Exit");

            Console.Write("Enter your choice: ");
            int choice;
            if (int.TryParse(Console.ReadLine(), out choice))
            {
                switch (choice)
                {
                    case 1:
                        Console.WriteLine("Inventory Details:");
                        item1.PrintDetails();
                        item2.PrintDetails();
                        break;
                    case 2:
                        Console.Write("Enter the quantity of laptops to sell: ");
                        int sellQuantityLaptops;
                        if (int.TryParse(Console.ReadLine(), out sellQuantityLaptops))
                        {
                            item1.SellItem(sellQuantityLaptops);
                        }
                        break;
                    case 3:
                        Console.Write("Enter the quantity of laptops to restock: ");
                        int restockQuantityLaptops;
                        if (int.TryParse(Console.ReadLine(), out restockQuantityLaptops))
                        {
                            item1.RestockItem(restockQuantityLaptops);
                        }
                        break;
                    case 4:
                        Console.Write("Enter the new price for the smartphone: ");
                        double newPriceSmartphone;
                        if (double.TryParse(Console.ReadLine(), out newPriceSmartphone))
                        {
                            item2.UpdatePrice(newPriceSmartphone);
                        }
                        break;
                    case 5:
                        Console.WriteLine($"Is {item2.ItemName} in stock? {item2.IsInStock()}");
                        break;
                    case 6:
                        exit = true;
                        break;
                    default:
                        Console.WriteLine("Invalid choice. Please enter a number between 1 and 6.");
                        break;
                }
            }
            else
            {
                Console.WriteLine("Invalid input. Please enter a valid number.");
            }

            Console.WriteLine();
        }

        Console.WriteLine("Exiting Inventory Management System.");
        Console.ReadLine();
    }
}

