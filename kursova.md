using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace курсова
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("rth");
            String BeginName = Console.ReadLine();
            Console.WriteLine("ryur");
            String EndName = Console.ReadLine();
            string[] way;
            int[] MinWay = new int[25];
            string[] city = { "Vinnuca", "Dnipropetrovsk", "Doneck", "Jitomir", "Zaporijja", "Ivano-frankivsk", "Kyiv", "Kirovograd", "Lugansk", "Lutsk", "Lviv", "Mikolaiv", "Odesa", "Poltava", "Rivne", "Simferopil", "Sumi", "ternopil", "Ujgorod", "Harkiv", "Herson", "Hmelnitskiy", "Cherkacy", "Chernivcy", "Chernigiv" };
            //масив відстаней між містами
            int[,] roads = {{0,0,0,126,0,0,266,317,0,0,0,466,429,0,313,0,0,0,0,0,0,122,340,312,0},{0,0,250,0,89,0,479,246,0,0,0,329,0,183,0,0,0,0,0,222,316,0,326,0,585},{0,0,0,0,243,0,0,0,151,0,0,0,0,391,0,571,0,0,0,283,535,0,0,0,0},{0,0,0,0,0,0,140,434,0,0,0,592,555,0,187,0,0,325,0,0,0,208,0,0,0}
            ,{0,0,0,0,0,0,0,314,0,0,0,352,0,0,0,371,0,0,0,303,292,0,0,0,0},{0,0,0,0,0,0,0,0,0,0,135,0,0,0,0,0,0,137,301,0,0,0,0,143,0},{0,0,0,0,0,0,0,299,0,0,0,517,480,343,0,0,339,0,0,0,0,0,201,0,151},{0,0,0,0,0,0,0,0,0,0,0,180,337,251,0,0,0,0,0,0,0,0,126,0,0},{0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,303,0,0,0,0,0}
            ,{0,0,0,0,0,0,0,0,0,0,152,0,0,0,70,0,0,164,0,0,0,0,0,0,0},{0,0,0,0,0,0,0,0,0,0,0,0,0,0,215,0,0,127,278,0,0,0,0,278,0},{0,0,0,0,0,0,0,0,0,0,0,0,134,0,0,0,0,0,0,0,71,0,0,0,0},{0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},{0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,185,0,0,144,0,0,271,0,412}
            ,{0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,158,0,0,0,195,0,0,0},{0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,279,0,0,0,0},{0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,185,0,0,343,0,338,},{0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,353,0,0,117,0,176,0},{0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,444,0}
            ,{0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},{0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},{0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,190,0},{0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,311},{0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},{0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0}};
            for (int i = 0; i < 25; i++)
                for (int j = 0; j < i; j++)
                {

                    roads[i, j] = roads[j, i];

                }
            /*  for (int i = 0; i < 25; i++)
              {
                  for (int j = 0; j < 25; j++)
                  {
                      Console.Write(roads[i, j] + " ");
                  }
                  Console.WriteLine();
              }*/
            int BeginNamber = 0, EndNamber = 0;
            while (city[BeginNamber] != BeginName)
                BeginNamber++;
            while (city[EndNamber] != EndName)
                EndNamber++;
            string NowName;
            int NowNamber = BeginNamber;
            // while (NowNamber != EndNamber)

            
                for (int i = 0; i < 25; i++)
                {
                    if ((roads[i, NowNamber] != 0) || (roads[i, NowNamber] > MinWay[i]))
                        MinWay[i] = MinWay[i] + roads[i, NowNamber];
                }
                for (int i = 0; i < 25; i++)
                    Console.Write(MinWay[i] + " ");

                for (int i = 0; i < 25; i++)
                {
                    if (MinWay[i] != 0)
 
                        NowNamber = MinWay[i];

                    if (NowNamber == EndNamber) break;
                    for ( int j = 0; j < 25; j++)
                    {
                        if ((roads[j, NowNamber] != 0) || (roads[j, NowNamber] > MinWay[j]))
                            MinWay[j] = MinWay[j] + roads[j, NowNamber];
                    }
                }

                for (int i = 0; i < 25; i++)
                    Console.Write(MinWay[i] + " ");






            /*int MinWay = 2000;
            int MinNamber=0;
            for (int i = 0; i < 25; i++)
                if ((roads[i, NowNamber] < MinWay)&(roads[i,NowNamber]!=0))
                {
                    MinWay = roads[i, NowNamber];
                    MinNamber = i;
                }
                    NowName=city[MinNamber];*/


            Console.Write(MinWay[EndNamber]);

            Console.ReadKey();
        }
    }
}
