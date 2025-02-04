# 姓名學筆記

## ChatGPT

根據《康熙字典》、姓名學的三才五格與五行(金、木、水、火、土)的關係。需要滿足以下所有條件：
一、姓名學五格靈動吉數的計算公式：

    1.天格 = 姓氏筆劃數 + 1。
    2.人格 = 姓氏筆劃數 + 中間名筆劃數。
    3.地格 = 中間名筆劃數 + 尾字筆劃數。
    4.外格 = 尾字筆劃數 + 1。
    5.總格 = 姓名所有字筆劃數總和。

二、靈動吉數：1、3、5、6、7、8、11、13、15、16、17、18、21、23、24、25、29、31、32、33、35、37、39、41、45、47、48、52、55、57、61、63、65、67、68、

姓氏「」，請提供合適的姓名清單。

## 程式碼 (C#)

直接將以下整片程式碼複製貼上 [.NET Fiddle](https://dotnetfiddle.net/) 後，點 Run

```csharp=
using System;
using System.Collections.Generic;

namespace ConsoleApp
{
    internal class Program
    {
        private static void Main(string[] args)
        {
            // 靈動吉數
            List<int> luckies = new List<int>
            {
                1, 3, 5, 6, 7, 8, 11, 13, 15, 16, 17, 18, 21, 23,
                24, 25, 29, 31, 32, 33, 35, 37, 39, 41, 45, 47,
                48, 52, 55, 57, 61, 63, 65, 67, 68, 81
            };

            // 五行及其對應的數字
            Dictionary<string, List<int>> fiveElements = new Dictionary<string, List<int>>()
            {
                { "木", new List<int> { 1, 2 } },
                { "火", new List<int> { 3, 4 } },
                { "土", new List<int> { 5, 6 } },
                { "金", new List<int> { 7, 8 } },
                { "水", new List<int> { 9, 0 } },
            };

            // 最大筆劃數
            int maxStrokes = 63;

            try
            {
                // x 姓氏的筆劃數
                Console.Write("請輸入姓氏筆劃數(以《康熙字典》筆劃為標準)：");
                int x = Convert.ToInt32(Console.ReadLine());

                Console.Write("請輸入人格五行(金、木、水、火、土)：");
                string manElement = Console.ReadLine();

                Console.Write("請輸入地格五行(金、木、水、火、土)：");
                string earthElement = Console.ReadLine();

                // y 中間名的筆劃數
                for (int y = 1; y <= maxStrokes; y++)
                {
                    // z 尾字的筆劃數
                    for (int z = 1; z <= maxStrokes; z++)
                    {
                        int heaven = x + 1;  // 天格 是先祖留傳下來的，其數理對人影響不大。
                        int man = x + y;     // 人格(姓名學吉兇之核心)
                        int earth = y + z;   // 地格
                        int outer = z + 1;   // 外格
                        int sum = x + y + z; // 總格

                        // 檢查條件
                        // 人格五行 && 地格五行 && 外格的吉數 && 總格的級數
                        if (fiveElements[manElement].Contains(man % 10) &&
                            fiveElements[earthElement].Contains(earth % 10) &&
                            luckies.Contains(outer) &&
                            luckies.Contains(sum))
                        {
                            Console.WriteLine($"中間名筆劃 {y,-2} 尾字筆劃 {z}");
                        }
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }

            Console.ReadLine();
        }
    }
}
```

## 參考

1. [不專業算名字 寶寶名字自己取](https://www.dcard.tw/f/parentchild/p/240431270)
2. [取名是種藝術跟技術，自己的寶寶名字自己取](https://shadindin.com/naming/取名是種藝術跟技術，自己的寶寶名字自己取)
3. [生肖蛇命名指南｜喜用字大全建議與忌用部首解析](https://1788lu.com/name-rename/newborn-baby-name-reference-library-by-year.html)
4. [名字測試評分](https://www.zhanbuwang.com/xingmingceshi_2.php)
5. [天地人三才配置](http://www.cdi.org.tw/name/n-3-water.html)
6. [生肖蛇取名宜忌：打造一生旺運好名字](https://1788lu.com/name-rename/newborn-baby-name-reference-library-by-year.html)

## 清單
