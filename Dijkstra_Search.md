		#include <vector>
		#include <set>
		using namespace std;
		
		struct edge 
		{ 
			int to;
			int	length; 
		};
		
		int dijkstra(const vector< vector<edge> > &graph, int source, int target, vector<int>& resultPath)
		{
			vector<int> min_distance(graph.saize(), INT_MAX);
			min_distance[source] = 0;
		
			set< pair<int, int> > active_vertices;
			active_vertices.insert({ 0, source });
		
			while (!active_vertices.empty())
			{
				int where = active_vertices.begin()->second;
		
				if (where == target)
				{	//목적지 도착 (목적지 인덱스부터 배열에서 거꾸로 거슬러 올라가면 경로가 나옴)
					return min_distance[where];
				}
		
				active_vertices.erase(active_vertices.begin());
		
				for (auto ed : graph[where])
				{
					if (min_distance[ed.to] > min_distance[where] + ed.length)
					{
						active_vertices.erase({ min_distance[ed.to], ed.to });
						min_distance[ed.to] = min_distance[where] + ed.length;
						active_vertices.insert({ min_distance[ed.to], ed.to });
						resultPath[ed.to] = where;
					}
				}
			}
			return INT_MAX;
		}
		
		void main()
		{
			vector<edge> vec0 = { { 1, 3 }, { 2, 1 } };	//0 -> 1로 가는 비용 3, 0 -> 2로가는데 비용 1
			vector<edge> vec1 = { { 2, 1 }, { 3, 4 } };
			vector<edge> vec2 = { { 1, 1 }, { 3, 6 } };
			vector<edge> vec3 = { { 1, 2 }, { 2, 4 } };
		
			vector< vector<edge> > graph;
			graph.push_back(vec0);
			graph.push_back(vec1);
			graph.push_back(vec2);
			graph.push_back(vec3);
		
			vector< int > path(graph.size(), -1);
			int ret = dijkstra(graph, 0, 3, path);	//0 -> 3으로 가는데 가장 짧은경로 찾기
			return;
		}
