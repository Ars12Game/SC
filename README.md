
#4:

internal class Program
{
    public static int DigitCount(int k)
    {
        int i = 1;
        for (; k >= 10; i++) k /= 10;
        return i;
    }

    public static int DigitN(int k, int n)
    {
        int i;
        for (i = 1; i <= n - 1; i++) k /= 10;
        if (k != 0) return k % 10;
        else return -1;
    }

    public static bool IsPalindrome(int k)
    {
        int len, i;
        len = DigitCount(k);
        for (i = 1; i <= len; i++)
            if (DigitN(k, i) != DigitN(k, len - i + 1)) return false;
        return true;
    }

    public static void Main(string[] args)
    {
        int i, k, count = 0;
        for (i = 1; i <= 10; ++i)
        {
            Console.Write("K:");
            string input = Console.ReadLine();
            if (int.TryParse(input, out k))
            {
                count += IsPalindrome(k) ? 1 : 0;
            }
            else
            {
                Console.WriteLine("Неверное значение.");
                i--;
            }

        }
        Console.WriteLine("Всего палиндромов: " + count);
    }
}
