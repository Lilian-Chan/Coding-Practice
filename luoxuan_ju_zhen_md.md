# 螺旋矩阵
---
Lintcode题目编号:374  
Leetcode题目编号：54
###**题目描述：**
给定一个包含 m x n 个要素的矩阵，（m 行, n 列），按照螺旋顺序，返回该矩阵中的所有要素。  
《剑指offer》中描述为：顺时针打印矩阵,无需返回  
样例  
>给定如下矩阵：
<br>
[
 [ 1, 2, 3 ],  
 [ 4, 5, 6 ],  
 [ 7, 8, 9 ]
]  
应返回 [1,2,3,6,9,8,7,4,5]。

###**解题思路：**  
###**测试用例**  
此题的注意点有：
1. 空向量
2. 只有一行的向量
3. 只有一列的向量  

| Test Case ID | Input | Expected Result |  
|: ---- :| -- | -- |  
| 1 | matrix中没有元素 | 程序不会崩溃，返回空向量 |  
| 2 | matrix为行列不等的矩阵<br>如<br>[ 1, 2, 3, 4 ], <br>[ 5, 6, 7, 8 ], <br>[ 9, 10, 11, 12 ] |[1,2,3,4,8,12,11,10,9,5,6,7] |  
| 3 | matrix为行列相等的矩阵<br>如<br>[ 1, 2, 3, 4 ], <br>[ 5, 6, 7, 8 ], <br>[ 9, 10, 11, 12 ],<br>[13, 14, 15, 16]  | [1,2,3,4,8,12,16,15,14,13,9,5,6,7,11,10] |  
|4| 只有一列的矩阵|[1,2,3]|  
|5|只有一行的矩阵|[1,2]|

###**复杂度：**  

###**代码1：**

```C++
class Solution {
public:
	/**
	* @param matrix a matrix of m x n elements
	* @return an integer array
	*/

	vector<int> spiralOrder(vector<vector<int>>& matrix)
	{
		// Write your code here

		
		vector<int> sipral;
		
		if (matrix.empty())
			return sipral;
			
		int startRow = 0;
		int endRow = matrix.size() - 1;
		int startColumn = 0;
		int endColumn = matrix[0].size() - 1;
		
		while (startRow <= endRow && startColumn <= endColumn)
		{
			
				for (int j = startColumn; j <= endColumn; ++j)
				{
					sipral.push_back(matrix[startRow][j]);
				}
				startRow++;
			
				for (int i = startRow; i <= endRow; ++i)
				{
					sipral.push_back(matrix[i][endColumn]);
				}
				endColumn--;
			

				if(startRow<=endRow)
				{ 
				    for(int j=endColumn;j >= startColumn;--j)
				    {
					    sipral.push_back(matrix[endRow][j]);
				    }
                }
                endRow--;
                
                
                if(startColumn<=endColumn)
                {
                    for(int i=endRow;i >= startRow;--i)
				    {
					    sipral.push_back(matrix[i][startColumn]);
				    }
                }
		        startColumn++;
		
		}
        return sipral;
	}
};

```



