---


---

<h2 id="quick-sort">Quick Sort</h2>
<h3 id="description">Description:</h3>
<p>QuickSort is a Divide and Conquer algorithm. It picks an element as pivot and partitions the given array around the picked pivot.  There are many different versions of quickSort that pick pivot in different ways.</p>
<ol>
<li>Always pick first element as pivot.</li>
<li>Always pick last element as pivot (implemented below)</li>
<li>Pick a random element as pivot.</li>
<li>Pick median as pivot.</li>
</ol>
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
<td><span class="katex--inline"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi mathvariant="normal">Ω</mi><mo stretchy="false">(</mo><mi>n</mi><mi>l</mi><mi>o</mi><mi>g</mi><mo stretchy="false">(</mo><mi>n</mi><mo stretchy="false">)</mo><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">Ω(n log(n))</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord">Ω</span><span class="mopen">(</span><span class="mord mathdefault">n</span><span class="mord mathdefault" style="margin-right: 0.01968em;">l</span><span class="mord mathdefault">o</span><span class="mord mathdefault" style="margin-right: 0.03588em;">g</span><span class="mopen">(</span><span class="mord mathdefault">n</span><span class="mclose">)</span><span class="mclose">)</span></span></span></span></span></td>
<td><span class="katex--inline"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi>θ</mi><mi mathvariant="normal">Ω</mi><mo stretchy="false">(</mo><mi>n</mi><mi>l</mi><mi>o</mi><mi>g</mi><mo stretchy="false">(</mo><mi>n</mi><mo stretchy="false">)</mo><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">θΩ(n log(n))</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathdefault" style="margin-right: 0.02778em;">θ</span><span class="mord">Ω</span><span class="mopen">(</span><span class="mord mathdefault">n</span><span class="mord mathdefault" style="margin-right: 0.01968em;">l</span><span class="mord mathdefault">o</span><span class="mord mathdefault" style="margin-right: 0.03588em;">g</span><span class="mopen">(</span><span class="mord mathdefault">n</span><span class="mclose">)</span><span class="mclose">)</span></span></span></span></span></td>
<td><span class="katex--inline"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>n</mi><mn>2</mn></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(n^2)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.06411em; vertical-align: -0.25em;"></span><span class="mord mathdefault" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathdefault">n</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span></td>
</tr>
</tbody>
</table><h3 id="diagram">Diagram:</h3>
<p>!https:///wksfsees.org/wp-content/uploads/gq/2014/01/QuickSort2.png)</p>
<h3 id="code">Code:</h3>
<p>In C++:</p>
<pre class=" language-c"><code class="prism ++ language-c"><span class="token comment">/* C++ implementation of QuickSort */</span>
<span class="token macro property">#<span class="token directive keyword">include</span> <span class="token string">&lt;bits/stdc++.h&gt;</span> </span>
using namespace std<span class="token punctuation">;</span> 

<span class="token comment">// A utility function to swap two elements </span>
<span class="token keyword">void</span> <span class="token function">swap</span><span class="token punctuation">(</span><span class="token keyword">int</span><span class="token operator">*</span> a<span class="token punctuation">,</span> <span class="token keyword">int</span><span class="token operator">*</span> b<span class="token punctuation">)</span> 
<span class="token punctuation">{</span> 
	<span class="token keyword">int</span> t <span class="token operator">=</span> <span class="token operator">*</span>a<span class="token punctuation">;</span> 
	<span class="token operator">*</span>a <span class="token operator">=</span> <span class="token operator">*</span>b<span class="token punctuation">;</span> 
	<span class="token operator">*</span>b <span class="token operator">=</span> t<span class="token punctuation">;</span> 
<span class="token punctuation">}</span> 

<span class="token comment">/* This function takes last element as pivot, places 
the pivot element at its correct position in sorted 
array, and places all smaller (smaller than pivot) 
to left of pivot and all greater elements to right 
of pivot */</span>
<span class="token keyword">int</span> <span class="token function">partition</span> <span class="token punctuation">(</span><span class="token keyword">int</span> arr<span class="token punctuation">[</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token keyword">int</span> low<span class="token punctuation">,</span> <span class="token keyword">int</span> high<span class="token punctuation">)</span> 
<span class="token punctuation">{</span> 
	<span class="token keyword">int</span> pivot <span class="token operator">=</span> arr<span class="token punctuation">[</span>high<span class="token punctuation">]</span><span class="token punctuation">;</span> <span class="token comment">// pivot </span>
	<span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token punctuation">(</span>low <span class="token operator">-</span> <span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">// Index of smaller element </span>

	<span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> j <span class="token operator">=</span> low<span class="token punctuation">;</span> j <span class="token operator">&lt;=</span> high <span class="token operator">-</span> <span class="token number">1</span><span class="token punctuation">;</span> j<span class="token operator">++</span><span class="token punctuation">)</span> 
	<span class="token punctuation">{</span> 
		<span class="token comment">// If current element is smaller than the pivot </span>
		<span class="token keyword">if</span> <span class="token punctuation">(</span>arr<span class="token punctuation">[</span>j<span class="token punctuation">]</span> <span class="token operator">&lt;</span> pivot<span class="token punctuation">)</span> 
		<span class="token punctuation">{</span> 
			i<span class="token operator">++</span><span class="token punctuation">;</span> <span class="token comment">// increment index of smaller element </span>
			<span class="token function">swap</span><span class="token punctuation">(</span><span class="token operator">&amp;</span>arr<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token operator">&amp;</span>arr<span class="token punctuation">[</span>j<span class="token punctuation">]</span><span class="token punctuation">)</span><span class="token punctuation">;</span> 
		<span class="token punctuation">}</span> 
	<span class="token punctuation">}</span> 
	<span class="token function">swap</span><span class="token punctuation">(</span><span class="token operator">&amp;</span>arr<span class="token punctuation">[</span>i <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token operator">&amp;</span>arr<span class="token punctuation">[</span>high<span class="token punctuation">]</span><span class="token punctuation">)</span><span class="token punctuation">;</span> 
	<span class="token keyword">return</span> <span class="token punctuation">(</span>i <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span> 
<span class="token punctuation">}</span> 

<span class="token comment">/* The main function that implements QuickSort 
arr[] --&gt; Array to be sorted, 
low --&gt; Starting index, 
high --&gt; Ending index */</span>
<span class="token keyword">void</span> <span class="token function">quickSort</span><span class="token punctuation">(</span><span class="token keyword">int</span> arr<span class="token punctuation">[</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token keyword">int</span> low<span class="token punctuation">,</span> <span class="token keyword">int</span> high<span class="token punctuation">)</span> 
<span class="token punctuation">{</span> 
	<span class="token keyword">if</span> <span class="token punctuation">(</span>low <span class="token operator">&lt;</span> high<span class="token punctuation">)</span> 
	<span class="token punctuation">{</span> 
		<span class="token comment">/* pi is partitioning index, arr[p] is now 
		at right place */</span>
		<span class="token keyword">int</span> pi <span class="token operator">=</span> <span class="token function">partition</span><span class="token punctuation">(</span>arr<span class="token punctuation">,</span> low<span class="token punctuation">,</span> high<span class="token punctuation">)</span><span class="token punctuation">;</span> 

		<span class="token comment">// Separately sort elements before </span>
		<span class="token comment">// partition and after partition </span>
		<span class="token function">quickSort</span><span class="token punctuation">(</span>arr<span class="token punctuation">,</span> low<span class="token punctuation">,</span> pi <span class="token operator">-</span> <span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span> 
		<span class="token function">quickSort</span><span class="token punctuation">(</span>arr<span class="token punctuation">,</span> pi <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">,</span> high<span class="token punctuation">)</span><span class="token punctuation">;</span> 
	<span class="token punctuation">}</span> 
<span class="token punctuation">}</span> 

<span class="token comment">/* Function to print an array */</span>
<span class="token keyword">void</span> <span class="token function">printArray</span><span class="token punctuation">(</span><span class="token keyword">int</span> arr<span class="token punctuation">[</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token keyword">int</span> size<span class="token punctuation">)</span> 
<span class="token punctuation">{</span> 
	<span class="token keyword">int</span> i<span class="token punctuation">;</span> 
	<span class="token keyword">for</span> <span class="token punctuation">(</span>i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> size<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> 
		cout <span class="token operator">&lt;&lt;</span> arr<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">&lt;&lt;</span> <span class="token string">" "</span><span class="token punctuation">;</span> 
	cout <span class="token operator">&lt;&lt;</span> endl<span class="token punctuation">;</span> 
<span class="token punctuation">}</span> 

<span class="token comment">// Driver Code </span>
<span class="token keyword">int</span> <span class="token function">main</span><span class="token punctuation">(</span><span class="token punctuation">)</span> 
<span class="token punctuation">{</span> 
	<span class="token keyword">int</span> arr<span class="token punctuation">[</span><span class="token punctuation">]</span> <span class="token operator">=</span> <span class="token punctuation">{</span><span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">7</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">}</span><span class="token punctuation">;</span> 
	<span class="token keyword">int</span> n <span class="token operator">=</span> <span class="token keyword">sizeof</span><span class="token punctuation">(</span>arr<span class="token punctuation">)</span> <span class="token operator">/</span> <span class="token keyword">sizeof</span><span class="token punctuation">(</span>arr<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span><span class="token punctuation">)</span><span class="token punctuation">;</span> 
	<span class="token function">quickSort</span><span class="token punctuation">(</span>arr<span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> n <span class="token operator">-</span> <span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span> 
	cout <span class="token operator">&lt;&lt;</span> <span class="token string">"Sorted array: \n"</span><span class="token punctuation">;</span> 
	<span class="token function">printArray</span><span class="token punctuation">(</span>arr<span class="token punctuation">,</span> n<span class="token punctuation">)</span><span class="token punctuation">;</span> 
	<span class="token keyword">return</span> <span class="token number">0</span><span class="token punctuation">;</span> 
<span class="token punctuation">}</span> 
</code></pre>
<p>In python:</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">def</span> <span class="token function">quick_sort</span><span class="token punctuation">(</span>sequence<span class="token punctuation">)</span><span class="token punctuation">:</span>  
    length <span class="token operator">=</span> <span class="token builtin">len</span><span class="token punctuation">(</span>sequence<span class="token punctuation">)</span>  
    smaller_arr <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>  
    greater_arr <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>  
    <span class="token keyword">if</span> length <span class="token operator">&lt;=</span> <span class="token number">1</span><span class="token punctuation">:</span>  
        <span class="token keyword">return</span> sequence  
    <span class="token keyword">else</span><span class="token punctuation">:</span>  
        pivot <span class="token operator">=</span> sequence<span class="token punctuation">.</span>pop<span class="token punctuation">(</span><span class="token punctuation">)</span>  <span class="token comment"># Get last element as pivot</span>
    <span class="token keyword">for</span> item <span class="token keyword">in</span> sequence<span class="token punctuation">:</span>  
        <span class="token keyword">if</span> item <span class="token operator">&lt;</span> pivot<span class="token punctuation">:</span>        <span class="token comment"># Comparsion between pivot and items in array</span>
            smaller_arr<span class="token punctuation">.</span>append<span class="token punctuation">(</span>item<span class="token punctuation">)</span>  
        <span class="token keyword">else</span><span class="token punctuation">:</span>  
            greater_arr<span class="token punctuation">.</span>append<span class="token punctuation">(</span>item<span class="token punctuation">)</span>  
    <span class="token comment"># Return sorted format: sorted smaller items + pivot + sorted greater items</span>
    <span class="token keyword">return</span> quick_sort<span class="token punctuation">(</span>smaller_arr<span class="token punctuation">)</span> <span class="token operator">+</span> <span class="token punctuation">[</span>pivot<span class="token punctuation">]</span> <span class="token operator">+</span> quick_sort<span class="token punctuation">(</span>greater_arr<span class="token punctuation">)</span>  
  
<span class="token keyword">print</span><span class="token punctuation">(</span>quick_sort<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">45</span><span class="token punctuation">,</span> <span class="token number">676</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">34</span><span class="token punctuation">,</span> <span class="token number">989</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">]</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
</code></pre>

