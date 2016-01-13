using System;
using ExpressionEvaluator;

namespace StarPadString
{
    class Program
    {
        static void Main(string[] args)
        {
           
            string xstars="**********";

            Stars(0, xstars, "l", "<= 10");
            Stars(10, xstars, "R", ">= 0");
            Stars(1, xstars, "l", "<= 9");
            Stars(10, xstars, "R", ">= 0");

            Console.Read();
        }

        private static void Stars( int x,  string xstars,string pm,string cnt)
        {
            bool result;
            do
            {           
                Console.WriteLine(xstars.Substring(0, x).PadLeft(10));
                x = pm == "l" ? x += 1 : x-=1;
                var expression = new CompiledExpression(x.ToString() + cnt);
                result = (bool) expression.Eval();
            } while (result);
            Console.WriteLine();
        }
 }
}

