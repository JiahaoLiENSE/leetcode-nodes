---


---

<h2 id="selection-sort">Selection Sort</h2>
<h3 id="description">Description:</h3>
<p>It is simple yet easy to implement technique in which we find the smallest element in the list and put it in its proper place. At each pass, the next smallest element is selected and placed in its proper position.</p>
<h3 id="runtime">Runtime:</h3>

<table>
<thead>
<tr>
<th></th>
<th>Best</th>
<th>Average</th>
<th>Worst</th>
</tr>
</thead>
<tbody>
<tr>
<td>Selection Sort</td>
<td><span class="katex--inline"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi mathvariant="normal">Ω</mi><mo stretchy="false">(</mo><msup><mi>n</mi><mn>2</mn></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">Ω(n^2)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.06411em; vertical-align: -0.25em;"></span><span class="mord">Ω</span><span class="mopen">(</span><span class="mord"><span class="mord mathdefault">n</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span></td>
<td><span class="katex--inline"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>n</mi><mn>2</mn></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(n^2)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.06411em; vertical-align: -0.25em;"></span><span class="mord mathdefault" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathdefault">n</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span></td>
<td><span class="katex--inline"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>n</mi><mn>2</mn></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(n^2)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.06411em; vertical-align: -0.25em;"></span><span class="mord mathdefault" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathdefault">n</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span></td>
</tr>
</tbody>
</table><h3 id="diagram">Diagram:</h3>
<p><img src="https://cdn.softwaretestinghelp.com/wp-content/qa/uploads/2019/06/Selection-Sort-Pass1.png" alt="1"><br>
<img src="https://cdn.softwaretestinghelp.com/wp-content/qa/uploads/2019/06/Selection-Sort-Pass2.png" alt="2"><br>
<img src="https://cdn.softwaretestinghelp.com/wp-content/qa/uploads/2019/06/Selection-Sort-Pass3.png" alt="3"></p>
<h3 id="code">Code:</h3>
<p>In C++:</p>
<pre class=" language-c"><code class="prism ++ language-c"><span class="token macro property">#<span class="token directive keyword">include</span> <span class="token string">&lt;bits/stdc++.h&gt;</span></span>
using namespace std<span class="token punctuation">;</span>

<span class="token keyword">void</span> <span class="token function">swap</span><span class="token punctuation">(</span><span class="token keyword">int</span> <span class="token operator">*</span>xp<span class="token punctuation">,</span><span class="token keyword">int</span> <span class="token operator">*</span>yp<span class="token punctuation">)</span>
<span class="token punctuation">{</span>
	<span class="token keyword">int</span> temp <span class="token operator">=</span> <span class="token operator">*</span>xp<span class="token punctuation">;</span>
	<span class="token operator">*</span>xp <span class="token operator">=</span> <span class="token operator">*</span>yp<span class="token punctuation">;</span>
	<span class="token operator">*</span>yp <span class="token operator">=</span> temp<span class="token punctuation">;</span>
<span class="token punctuation">}</span>

<span class="token keyword">void</span> <span class="token function">selectionSort</span><span class="token punctuation">(</span><span class="token keyword">int</span> arr<span class="token punctuation">[</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token keyword">int</span> n<span class="token punctuation">)</span>
<span class="token punctuation">{</span>
	<span class="token keyword">int</span> i<span class="token punctuation">,</span> j<span class="token punctuation">,</span> min_idx<span class="token punctuation">;</span>
	<span class="token comment">// One by one move boundary of unsorted subarray`</span>
	<span class="token keyword">for</span> <span class="token punctuation">(</span>i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> n<span class="token number">-1</span><span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span>
	<span class="token punctuation">{</span>
		<span class="token comment">// Find the minimum element in unsorted array`</span>
		min_idx <span class="token operator">=</span> i<span class="token punctuation">;</span>
		<span class="token keyword">for</span> <span class="token punctuation">(</span>j <span class="token operator">=</span> i<span class="token operator">+</span><span class="token number">1</span><span class="token punctuation">;</span> j <span class="token operator">&lt;</span> n<span class="token punctuation">;</span> j<span class="token operator">++</span><span class="token punctuation">)</span>
			<span class="token keyword">if</span> <span class="token punctuation">(</span>arr<span class="token punctuation">[</span>j<span class="token punctuation">]</span> <span class="token operator">&lt;</span> arr<span class="token punctuation">[</span>min_idx<span class="token punctuation">]</span><span class="token punctuation">)</span>
				min_idx <span class="token operator">=</span> j<span class="token punctuation">;</span>
		<span class="token comment">// Swap the found minimum element with the first element`</span>
		<span class="token function">swap</span><span class="token punctuation">(</span><span class="token operator">&amp;</span>arr<span class="token punctuation">[</span>min_idx<span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token operator">&amp;</span>arr<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
<span class="token comment">/* Function to print an array */</span>
<span class="token keyword">void</span> <span class="token function">printArray</span><span class="token punctuation">(</span><span class="token keyword">int</span> arr<span class="token punctuation">[</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token keyword">int</span> size<span class="token punctuation">)</span>
<span class="token punctuation">{</span>
	<span class="token keyword">int</span> i<span class="token punctuation">;</span>
	<span class="token keyword">for</span> <span class="token punctuation">(</span>i<span class="token operator">=</span><span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> size<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span>
	cout <span class="token operator">&lt;&lt;</span> arr<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">&lt;&lt;</span> <span class="token string">" "</span><span class="token punctuation">;</span>
	cout <span class="token operator">&lt;&lt;</span> endl<span class="token punctuation">;</span>
<span class="token punctuation">}</span>
<span class="token comment">// Driver program to test above functions`</span>
<span class="token keyword">int</span> <span class="token function">main</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
<span class="token punctuation">{</span>
	<span class="token keyword">int</span> arr<span class="token punctuation">[</span><span class="token punctuation">]</span> <span class="token operator">=</span> <span class="token punctuation">{</span><span class="token number">64</span><span class="token punctuation">,</span> <span class="token number">25</span><span class="token punctuation">,</span> <span class="token number">12</span><span class="token punctuation">,</span> <span class="token number">22</span><span class="token punctuation">,</span> <span class="token number">11</span><span class="token punctuation">}</span><span class="token punctuation">;</span>
	<span class="token keyword">int</span> n <span class="token operator">=</span> <span class="token keyword">sizeof</span><span class="token punctuation">(</span>arr<span class="token punctuation">)</span><span class="token operator">/</span><span class="token keyword">sizeof</span><span class="token punctuation">(</span>arr<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token function">selectionSort</span><span class="token punctuation">(</span>arr<span class="token punctuation">,</span> n<span class="token punctuation">)</span><span class="token punctuation">;</span>
	cout <span class="token operator">&lt;&lt;</span> <span class="token string">"Sorted array: \n"</span><span class="token punctuation">;</span>
	<span class="token function">printArray</span><span class="token punctuation">(</span>arr<span class="token punctuation">,</span> n<span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token keyword">return</span> <span class="token number">0</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>In python:</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">def</span> <span class="token function">selection_sort</span><span class="token punctuation">(</span>collection<span class="token punctuation">)</span><span class="token punctuation">:</span>
	<span class="token triple-quoted-string string">"""Pure implementation of the selection sort algorithm in Python
	:param collection: some mutable ordered collection with heterogeneous
	comparable items inside
	:return: the same collection ordered by ascending
	Examples:
	&gt;&gt;&gt; selection_sort([0, 5, 3, 2, 2])
	[0, 2, 2, 3, 5]
	&gt;&gt;&gt; selection_sort([])
	[]
	&gt;&gt;&gt; selection_sort([-2, -5, -45])
	[-45, -5, -2]
	"""</span>
	length <span class="token operator">=</span> <span class="token builtin">len</span><span class="token punctuation">(</span>collection<span class="token punctuation">)</span>
	<span class="token keyword">for</span> i <span class="token keyword">in</span> <span class="token builtin">range</span><span class="token punctuation">(</span>length <span class="token operator">-</span> <span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
		least <span class="token operator">=</span> i
		<span class="token keyword">for</span> k <span class="token keyword">in</span> <span class="token builtin">range</span><span class="token punctuation">(</span>i <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">,</span> length<span class="token punctuation">)</span><span class="token punctuation">:</span>
			<span class="token keyword">if</span> collection<span class="token punctuation">[</span>k<span class="token punctuation">]</span> <span class="token operator">&lt;</span> collection<span class="token punctuation">[</span>least<span class="token punctuation">]</span><span class="token punctuation">:</span>
				least <span class="token operator">=</span> k
		<span class="token keyword">if</span> least <span class="token operator">!=</span> i<span class="token punctuation">:</span>
			collection<span class="token punctuation">[</span>least<span class="token punctuation">]</span><span class="token punctuation">,</span> collection<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">=</span> <span class="token punctuation">(</span>collection<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">,</span> collection<span class="token punctuation">[</span>least<span class="token punctuation">]</span><span class="token punctuation">)</span>
	<span class="token keyword">return</span> collection
	
<span class="token keyword">if</span> __name__ <span class="token operator">==</span> <span class="token string">"__main__"</span><span class="token punctuation">:</span>
	user_input <span class="token operator">=</span> <span class="token builtin">input</span><span class="token punctuation">(</span><span class="token string">"Enter numbers separated by a comma:\n"</span><span class="token punctuation">)</span><span class="token punctuation">.</span>strip<span class="token punctuation">(</span><span class="token punctuation">)</span>
	unsorted <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token builtin">int</span><span class="token punctuation">(</span>item<span class="token punctuation">)</span> <span class="token keyword">for</span> item <span class="token keyword">in</span> user_input<span class="token punctuation">.</span>split<span class="token punctuation">(</span><span class="token string">","</span><span class="token punctuation">)</span><span class="token punctuation">]</span>
	<span class="token keyword">print</span><span class="token punctuation">(</span>selection_sort<span class="token punctuation">(</span>unsorted<span class="token punctuation">)</span><span class="token punctuation">)</span>
</code></pre>

