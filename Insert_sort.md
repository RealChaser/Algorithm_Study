삽입정렬

<https://www.youtube.com/watch?v=ROalU379l3U>

	
	#include <iostream>
	using namespace std;
	
	void main()
	{
		int data[] = {3, 6, 2, 5, 1, 4};
		int count = sizeof(data) / sizeof(data[0]);
			
		for(int i = 1; i < count; ++i)
		{
			for(int j = i; j > 0; )
			{
				if(data[j-1] > data[j])
				{
					int temp = data[j-1];
					data[j-1] = data[j];
					data[j] = temp;	
					--j;
				}
				else
				{
					break;
				}
			}		
		}
	
		for(int i = 0; i < count; ++i)
		{
			cout << data[i] << endl;
		}	
	}