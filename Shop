import java.util.Scanner;

public class Shop {
	/////////////////// Class Object /////////////////////////////
	public static class userShop {

		public boolean isCreated = false, hasBought = false;
		public String[] names;
		public Float[] prices;
		public int[] amounts;
		public double discount;
		public float discountRate;

		public void setArrays(String[] names, Float[] prices, double discount, float discountRate) {
			this.names = new String[names.length];
			this.prices = new Float[prices.length];
			this.amounts = new int[names.length];
			for (int i = 0; i < names.length; i++) {
				this.names[i] = names[i];
				this.prices[i] = prices[i];
			}
			this.discount = discount;
			this.discountRate = discountRate;
			isCreated = true;
		}
		public void setAmounts(int[] amounts) {
			for (int i = 0; i < amounts.length; i++) 
				this.amounts[i] = amounts[i];
			hasBought = true;
		}
		public String getName(int setNum) {
			return names[setNum];
		}
		public Float getPrice(int setNum) {
			return prices[setNum];
		}
		public int getAmount(int setNum) {
			return amounts[setNum];
		}
		public int getSize() {
			return names.length;
		}

	}	
	/////////////////// Main /////////////////////////////	
	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		input.useDelimiter(System.getProperty("line.separator"));
		userShop userShop = new userShop();
		boolean end = false;
		int choice;
		int amount = 0;
		float price = 0;
		String name;
		while (!end) {

			System.out.println("This program supports 4 functions:");
			System.out.println("	1. Setup shop");
			System.out.println("	2. Buy");
			System.out.println("	3. List Items");
			System.out.println("	4. Checkout");
			System.out.print("Please choose the function you want: ");
			choice = input.nextInt();
			System.out.println();

			if (choice == 1) {

				System.out.print("Please enter the number of items: ");
				int numItems = input.nextInt();
				String[] names = new String[numItems];
				Float[] prices = new Float[numItems];

				for (int i = 0; i < numItems; i++) {
					System.out.print("Enter name of product " + i + ": ");
					names[i] = input.next();
					System.out.print("Enter price of product" + i + ": ");
					prices[i] = input.nextFloat();
				}

				System.out.print("Please enter the amount to qualify for discount: ");
				double discount = input.nextDouble();
				System.out.print("Please enter the discount rate (0.1 for 10%): ");
				float discountRate = input.nextFloat();

				userShop.setArrays(names, prices, discount, discountRate);
				System.out.println();

			}
			else if (choice == 2) {
				if (userShop.isCreated) {
					int[] amounts = new int[userShop.getSize()];
					for (int i = 0; i < userShop.getSize(); i++) {
						System.out.print("Enter the amount of " + userShop.getName(i) + ": ");
						amounts[i] = input.nextInt();
					}
					userShop.setAmounts(amounts);

				}
				else
					System.out.println("Shop is not setup yet!");
				System.out.println();
			}
			else if (choice == 3) {
				if (userShop.hasBought) {

					for (int i = 0; i < userShop.getSize(); i++) {
						amount = userShop.getAmount(i);
						price = userShop.getPrice(i);
						name = userShop.getName(i);
						System.out.println(amount + " count of " + name + " @ " + price + " = $" + (amount * price) );
					}
				}
				if (!userShop.isCreated) 
					System.out.println("Shop is not setup yet!");
				if (!userShop.hasBought)
						System.out.println("Try again: You have not bought anything");
				System.out.println();

			}
			else if (choice == 4) {
				if (userShop.hasBought && userShop.isCreated) {
					float subTotal = 0;
					for (int i = 0; i < userShop.getSize(); i++) {
						amount = userShop.getAmount(i);
						price = userShop.getPrice(i);
						subTotal += (amount * price);
					}
					float discount = 0;
					System.out.println("Thanks for coming!");
					System.out.println("Sub Total:	$" + subTotal);
					if (subTotal > userShop.discount)
						discount = userShop.discountRate * subTotal;
					System.out.println("-Discount:	$" + discount);
					System.out.println("Total:	$" + (subTotal - discount));

					end = true;
					input.close();
				}
				if (!userShop.hasBought)
					System.out.println("Try again: You have not bought anything");
				if (!userShop.isCreated)
					System.out.println("Shop is not setup yet!");
				System.out.println();
			}
			else
				System.out.println("Error: Do not know " + choice);
		}

	}

}
