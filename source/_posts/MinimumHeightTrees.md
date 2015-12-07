## [Leetcode] Minimum Height Trees
<div style="-webkit-text-stroke-width: 0px; background-color: white; box-sizing: border-box; color: #333333; font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 30px; margin: 0px 0px 10px; orphans: auto; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 1; word-spacing: 0px;">
For a undirected graph with tree characteristics, we can choose any node as the root. The result graph is then a rooted tree. Among all possible rooted trees, those with minimum height are called minimum height trees (MHTs). Given such a graph, write a function to find all the MHTs and return a list of their root labels.</div>
<div style="-webkit-text-stroke-width: 0px; background-color: white; box-sizing: border-box; color: #333333; font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 30px; margin: 0px 0px 10px; orphans: auto; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 1; word-spacing: 0px;">

The graph contains<span class="Apple-converted-space">&nbsp;</span><code style="background-color: #f9f2f4; border-radius: 4px; box-sizing: border-box; color: #c7254e; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 12.6px; padding: 2px 4px;">n</code><span class="Apple-converted-space">&nbsp;</span>nodes which are labeled from<span class="Apple-converted-space">&nbsp;</span><code style="background-color: #f9f2f4; border-radius: 4px; box-sizing: border-box; color: #c7254e; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 12.6px; padding: 2px 4px;">0</code><span class="Apple-converted-space">&nbsp;</span>to<span class="Apple-converted-space">&nbsp;</span><code style="background-color: #f9f2f4; border-radius: 4px; box-sizing: border-box; color: #c7254e; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 12.6px; padding: 2px 4px;">n - 1</code>. You will be given the number<span class="Apple-converted-space">&nbsp;</span><code style="background-color: #f9f2f4; border-radius: 4px; box-sizing: border-box; color: #c7254e; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 12.6px; padding: 2px 4px;">n</code><span class="Apple-converted-space">&nbsp;</span>and a list of undirected<span class="Apple-converted-space">&nbsp;</span><code style="background-color: #f9f2f4; border-radius: 4px; box-sizing: border-box; color: #c7254e; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 12.6px; padding: 2px 4px;">edges</code><span class="Apple-converted-space">&nbsp;</span>(each edge is a pair of labels).</div>
<div style="-webkit-text-stroke-width: 0px; background-color: white; box-sizing: border-box; color: #333333; font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 30px; margin: 0px 0px 10px; orphans: auto; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 1; word-spacing: 0px;">
You can assume that no duplicate edges will appear in<span class="Apple-converted-space">&nbsp;</span><code style="background-color: #f9f2f4; border-radius: 4px; box-sizing: border-box; color: #c7254e; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 12.6px; padding: 2px 4px;">edges</code>. Since all edges are undirected,<span class="Apple-converted-space">&nbsp;</span><code style="background-color: #f9f2f4; border-radius: 4px; box-sizing: border-box; color: #c7254e; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 12.6px; padding: 2px 4px;">[0, 1]</code><span class="Apple-converted-space">&nbsp;</span>is the same as<span class="Apple-converted-space">&nbsp;</span><code style="background-color: #f9f2f4; border-radius: 4px; box-sizing: border-box; color: #c7254e; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 12.6px; padding: 2px 4px;">[1, 0]</code><span class="Apple-converted-space">&nbsp;</span>and thus will not appear together in<span class="Apple-converted-space">&nbsp;</span><code style="background-color: #f9f2f4; border-radius: 4px; box-sizing: border-box; color: #c7254e; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 12.6px; padding: 2px 4px;">edges</code>.</div>
<div style="-webkit-text-stroke-width: 0px; background-color: white; box-sizing: border-box; color: #333333; font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 30px; margin: 0px 0px 10px; orphans: auto; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 1; word-spacing: 0px;">
<b style="box-sizing: border-box; font-weight: 700;">Example 1:</b></div>
<div style="-webkit-text-stroke-width: 0px; background-color: white; box-sizing: border-box; color: #333333; font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 30px; margin: 0px 0px 10px; orphans: auto; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 1; word-spacing: 0px;">
Given<span class="Apple-converted-space">&nbsp;</span><code style="background-color: #f9f2f4; border-radius: 4px; box-sizing: border-box; color: #c7254e; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 12.6px; padding: 2px 4px;">n = 4</code>,<span class="Apple-converted-space">&nbsp;</span><code style="background-color: #f9f2f4; border-radius: 4px; box-sizing: border-box; color: #c7254e; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 12.6px; padding: 2px 4px;">edges = [[1, 0], [1, 2], [1, 3]]</code></div>
<pre style="-webkit-text-stroke-width: 0px; background-color: whitesmoke; border-radius: 4px; border: 1px solid rgb(204, 204, 204); box-sizing: border-box; color: #333333; display: block; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 13px; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 1.42857; margin: 0px 0px 10px; orphans: auto; overflow: auto; padding: 9.5px; text-align: start; text-indent: 0px; text-transform: none; widows: 1; word-break: break-all; word-spacing: 0px; word-wrap: break-word;">        0
        |
        1
       / \
      2   3
</pre>
<div style="-webkit-text-stroke-width: 0px; background-color: white; box-sizing: border-box; color: #333333; font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 30px; margin: 0px 0px 10px; orphans: auto; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 1; word-spacing: 0px;">
return<span class="Apple-converted-space">&nbsp;</span><code style="background-color: #f9f2f4; border-radius: 4px; box-sizing: border-box; color: #c7254e; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 12.6px; padding: 2px 4px;">[1]</code></div>
<div style="-webkit-text-stroke-width: 0px; background-color: white; box-sizing: border-box; color: #333333; font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 30px; margin: 0px 0px 10px; orphans: auto; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 1; word-spacing: 0px;">
<b style="box-sizing: border-box; font-weight: 700;">Example 2:</b></div>
<div style="-webkit-text-stroke-width: 0px; background-color: white; box-sizing: border-box; color: #333333; font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 30px; margin: 0px 0px 10px; orphans: auto; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 1; word-spacing: 0px;">
Given<span class="Apple-converted-space">&nbsp;</span><code style="background-color: #f9f2f4; border-radius: 4px; box-sizing: border-box; color: #c7254e; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 12.6px; padding: 2px 4px;">n = 6</code>,<span class="Apple-converted-space">&nbsp;</span><code style="background-color: #f9f2f4; border-radius: 4px; box-sizing: border-box; color: #c7254e; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 12.6px; padding: 2px 4px;">edges = [[0, 3], [1, 3], [2, 3], [4, 3], [5, 4]]</code></div>
<pre style="-webkit-text-stroke-width: 0px; background-color: whitesmoke; border-radius: 4px; border: 1px solid rgb(204, 204, 204); box-sizing: border-box; color: #333333; display: block; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 13px; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 1.42857; margin: 0px 0px 10px; orphans: auto; overflow: auto; padding: 9.5px; text-align: start; text-indent: 0px; text-transform: none; widows: 1; word-break: break-all; word-spacing: 0px; word-wrap: break-word;">     0  1  2
      \ | /
        3
        |
        4
        |
        5
</pre>
<div style="-webkit-text-stroke-width: 0px; background-color: white; box-sizing: border-box; color: #333333; font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 30px; margin: 0px 0px 10px; orphans: auto; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 1; word-spacing: 0px;">
return<span class="Apple-converted-space">&nbsp;</span><code style="background-color: #f9f2f4; border-radius: 4px; box-sizing: border-box; color: #c7254e; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 12.6px; padding: 2px 4px;">[3, 4]</code></div>
<br />
<h4>
Analysis:</h4>
The first thought is permuting the whole graph and depth first traversal them. But exceeding the time limit.<br />
The second solution is from other guys (<a href="http://bookshadow.com/weblog/2015/11/26/leetcode-minimum-height-trees/">http://bookshadow.com/weblog/2015/11/26/leetcode-minimum-height-trees/</a>), very elegant.<br />
Its thought is to eliminate the leaves and remove the edge connected to leaves and add the newly leaves to a list. Finally the remaining node is the roots we want which are less or equal to two.<br />
<br />
<h4>
Solution 1 </h4>
<h4>
Time Complexity:</h4>
<h5>O(n^2)</h5><br />
<br />
<pre style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"><code style="color: black; word-wrap: normal;"> class VertexNode {  
 public:  
      VertexNode(int num) : label(num) {};  
      int label;  
      vector&lt;int&gt; edges;  
 };  
 class Solution {  
 public:  
      void buildAdjcentList(vector&lt;pair&lt;int, int&gt;&gt;&amp; edges, unordered_map&lt;int, VertexNode*&gt; &amp; adjList)  
      {  
           for (pair&lt;int, int&gt; p : edges)  
           {  
                VertexNode * newnode1, *newnode2;  
                if (adjList.find(p.first) == adjList.end())  
                {  
                     newnode1 = new VertexNode(p.first);  
                     adjList[p.first] = newnode1;  
                }  
                else  
                {  
                     newnode1 = adjList[p.first];  
                }  
                if (adjList.find(p.second) == adjList.end())  
                {  
                     newnode2 = new VertexNode(p.second);  
                     adjList[p.second] = newnode2;  
                }  
                else  
                {  
                     newnode2 = adjList[p.second];  
                }  
                newnode1-&gt;edges.push_back(newnode2-&gt;label);  
                newnode2-&gt;edges.push_back(newnode1-&gt;label);  
           }  
      }  
      void DFSMHT(unordered_map&lt;int, VertexNode*&gt; &amp; adjList, int curlabel, int prevlabel, int depth, int &amp; minDepth)  
      {  
           VertexNode * curNode = adjList[curlabel];  
           if (!curNode) return;  
           if (curNode-&gt;edges.size() == 1 &amp;&amp; curNode-&gt;edges[0] == prevlabel)  
           {  
                if (minDepth &gt; depth)  
                {  
                     minDepth = depth;  
                }  
                return;  
           }  
           for (int i : curNode-&gt;edges)  
           {  
             if (i == prevlabel) continue;  
                DFSMHT(adjList, i, curNode-&gt;label, depth+1, minDepth);  
           }  
      }  
   vector&lt;int&gt; findMinHeightTrees(int n, vector&lt;pair&lt;int, int&gt;&gt;&amp; edges) {  
        unordered_map&lt;int, VertexNode*&gt; adjList;  
        buildAdjcentList(edges, adjList);  
        int minDepth = INT_MAX;  
        int curdepth = INT_MAX;  
        vector&lt;int&gt; retList;  
        for (pair&lt;int, VertexNode*&gt; it : adjList)  
        {  
             DFSMHT(adjList, it.second-&gt;label, -1, 1, curdepth);  
             if (curdepth &lt;= minDepth)  
             {  
                  if (curdepth &lt; minDepth)  
                       retList.clear();  
                  retList.push_back(it.second-&gt;label);  
                  minDepth = curdepth;  
             }  
             curdepth = INT_MAX;  
        }  
        return retList;  
   }  
 };  
</code></pre>
<br />
<br />
<h4>
Solution 2</h4>
<h4>
Time Complexity:</h4>
<h5>O(n)</h5>
<br />
<br />
<pre style="background-image: URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif); background: #f0f0f0; border: 1px dashed #CCCCCC; color: black; font-family: arial; font-size: 12px; height: auto; line-height: 20px; overflow: auto; padding: 0px; text-align: left; width: 99%;"><code style="color: black; word-wrap: normal;"> class Solution(object):  
   def findMinHeightTrees(self, n, edges):  
     """  
     :type n: int  
     :type edges: List[List[int]]  
     :rtype: List[int]  
     """  
     children = collections.defaultdict(set)  
     for x, y in edges:  
          children[x].add(y)  
          children[y].add(x)  
     vertices = set(children.keys())  
     while len(vertices) &gt; 2:  
          leaves = [x for x in children if len(children[x]) == 1]  
          for x in leaves:  
               for y in children[x]:  
                    children[y].remove(x)  
               del children[x]  
               vertices.remove(x)  
     return list(vertices) if n != 1 else [0]  
</code></pre>
