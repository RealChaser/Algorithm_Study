거품정렬

<https://www.youtube.com/watch?v=ebI54DXYQG8>

	
	#include <iostream>
	using namespace std;
	
	void main()
	{
		int data[] = {3, 6, 2, 5, 1, 4};
		int count = sizeof(data) / sizeof(data[0]);
		
		for(int i = 0; i < count - 1; ++i)
		{
			for(int j = 0; j < count - 1 - i; ++j)
			{
				if(data[j] > data[j + 1])
				{
					int temp = data[j + 1];
					data[j + 1] = data[j];
					data[j] = temp;
				}
			}
		}
	
		for(int i = 0; i < count; ++i)
		{
			cout << data[i] << endl;
		}
	}