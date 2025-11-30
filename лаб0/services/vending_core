using VendingMachineApp.Models;

namespace VendingMachineApp.Services
{
    public class VendingMachine
    {
        private List<Product> products;
        private int insertedMoney;
        private int collectedMoney;
        public VendingMachine()
        {
            products = new List<Product>
            {
                new Product("Вода", 5000, 5), 
                new Product("Чай", 7000, 3),  
                new Product("Кофе", 10000, 4),
                new Product("Сок", 8500, 2)   
            };
            insertedMoney = 0;
            collectedMoney = 0;
        }

        public void ShowProducts()
        {
            Console.WriteLine("\n--- Список товаров ---");
            for (int i = 0; i < products.Count; i++)
            {
                Console.WriteLine($"{i + 1}. {products[i]}");
            }
        }

        public void InsertCoin(Coin coin)
        {
            insertedMoney += coin.Value;
            Console.WriteLine($"Вы внесли {coin.Value / 100.0:F2} руб. (Всего: {insertedMoney / 100.0:F2} руб.)");
        }

        public void BuyProduct(int index)
        {
            if (index < 1 || index > products.Count)
            {
                Console.WriteLine("Такого товара нет.");
                return;
            }

            var product = products[index - 1];

            if (product.Amound <= 0)
            {
                Console.WriteLine("Товар закончился!");
                return;
            }

            if (insertedMoney < product.Price)
            {
                Console.WriteLine($"Недостаточно средств. Нужно ещё {(product.Price - insertedMoney) / 100.0:F2} руб.");
                return;
            }

            insertedMoney -= product.Price;
            collectedMoney += product.Price;
            product.Amound--;

            Console.WriteLine($"Вы купили: {product.Name}. Спасибо за покупку!");
        }

        public void GiveChange()
        {
            if (insertedMoney > 0)
            {
                Console.WriteLine($"Ваша сдача: {insertedMoney / 100.0:F2} руб.");
                insertedMoney = 0;
            }
            else
            {
                Console.WriteLine("Сдачи нет.");
            }
        }

        public void Restock(int index, int amound)
        {
            if (index < 1 || index > products.Count) return;
            products[index - 1].Amound += amound;
        }

        public void CollectMoney()
        {
            Console.WriteLine($"Админ забрал {collectedMoney / 100.0:F2} руб.");
            collectedMoney = 0;
        }
		public int GetBalance()
		{
    		return insertedMoney;	
		}
    }
}
