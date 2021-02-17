---


---

<h2 id="bubble-sort">Bubble Sort</h2>
<h3 id="description">Description:</h3>
<p>Bubble sort is the simplest technique in which we compare every element with its adjacent element and swap the elements if they are not in order. This way at the end of every iteration (called a pass), the heaviest element gets bubbled up at the end of the list.</p>
<h3 id="runtime">Runtime:</h3>
<p>bubble sort performs <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><mi>n</mi><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(n)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathdefault" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord mathdefault">n</span><span class="mclose">)</span></span></span></span></span> operations on an <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><mi>n</mi><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(n)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathdefault" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord mathdefault">n</span><span class="mclose">)</span></span></span></span></span> number of elements, leading to a total running time of <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>n</mi><mn>2</mn></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(n^2)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.06411em; vertical-align: -0.25em;"></span><span class="mord mathdefault" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathdefault">n</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span>.</p>

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
<td><span class="katex--inline"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi mathvariant="normal">Ω</mi><mi>O</mi><mo stretchy="false">(</mo><mi>n</mi><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">ΩO(n)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord">Ω</span><span class="mord mathdefault" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord mathdefault">n</span><span class="mclose">)</span></span></span></span></span></td>
<td><span class="katex--inline"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>n</mi><mn>2</mn></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(n^2)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.06411em; vertical-align: -0.25em;"></span><span class="mord mathdefault" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathdefault">n</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span></td>
<td><span class="katex--inline"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><msup><mi>n</mi><mn>2</mn></msup><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(n^2)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1.06411em; vertical-align: -0.25em;"></span><span class="mord mathdefault" style="margin-right: 0.02778em;">O</span><span class="mopen">(</span><span class="mord"><span class="mord mathdefault">n</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.814108em;"><span class="" style="top: -3.063em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mclose">)</span></span></span></span></span></td>
</tr>
</tbody>
</table><h3 id="diagram">Diagram:</h3>
<p><img src="https://cdn.softwaretestinghelp.com/wp-content/qa/uploads/2019/06/bubble-sort-Pass1.png" alt="1"><br>
<img src="https://cdn.softwaretestinghelp.com/wp-content/qa/uploads/2019/06/bubble-sort-Pass2.png" alt="2"><br>
<img src="https://cdn.softwaretestinghelp.com/wp-content/qa/uploads/2019/06/bubble-sort-Pass3.png" alt="3"></p>
<h3 id="code">Code:</h3>
<p>In C++:</p>
<pre class=" language-c"><code class="prism ++ language-c"><span class="token macro property">#<span class="token directive keyword">include</span><span class="token string">&lt;iostream&gt;</span></span>
using namespace std<span class="token punctuation">;</span>

<span class="token keyword">int</span> <span class="token function">main</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
	<span class="token keyword">int</span> i<span class="token punctuation">,</span>j<span class="token punctuation">,</span>temp<span class="token punctuation">;</span>
	<span class="token keyword">int</span> a<span class="token punctuation">[</span><span class="token number">5</span><span class="token punctuation">]</span><span class="token operator">=</span><span class="token punctuation">[</span><span class="token number">10</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">0</span><span class="token punctuation">,</span><span class="token number">43</span><span class="token punctuation">,</span><span class="token number">12</span><span class="token punctuation">]</span><span class="token punctuation">;</span>
	cout <span class="token operator">&lt;&lt;</span><span class="token string">"Input list..."</span><span class="token punctuation">;</span>
	<span class="token keyword">for</span> <span class="token punctuation">(</span>i<span class="token operator">=</span><span class="token number">0</span><span class="token punctuation">;</span> i<span class="token operator">&lt;</span><span class="token number">5</span><span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		cout<span class="token operator">&lt;&lt;</span>a<span class="token punctuation">[</span><span class="token number">5</span><span class="token punctuation">]</span><span class="token operator">&lt;&lt;</span><span class="token string">"\t"</span><span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
	cout<span class="token operator">&lt;&lt;</span>endl<span class="token punctuation">;</span>
	<span class="token keyword">for</span><span class="token punctuation">(</span>i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i<span class="token operator">&lt;</span><span class="token number">5</span><span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		<span class="token keyword">for</span><span class="token punctuation">(</span>j <span class="token operator">=</span> i<span class="token operator">+</span><span class="token number">1</span><span class="token punctuation">;</span> j<span class="token operator">&lt;</span><span class="token number">5</span><span class="token punctuation">;</span> j<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
			<span class="token keyword">if</span><span class="token punctuation">(</span>a<span class="token punctuation">[</span>j<span class="token punctuation">]</span> <span class="token operator">&lt;</span> a<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
				temp<span class="token operator">=</span>a<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">;</span>
				a<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token operator">=</span>a<span class="token punctuation">[</span>j<span class="token punctuation">]</span><span class="token punctuation">;</span>
				a<span class="token punctuation">[</span>j<span class="token punctuation">]</span><span class="token operator">=</span>temp<span class="token punctuation">;</span>
			<span class="token punctuation">}</span>
		<span class="token punctuation">}</span>
	<span class="token punctuation">}</span>
	cout <span class="token operator">&lt;&lt;</span><span class="token string">"Sorted Element List ...\n"</span><span class="token punctuation">;</span>
	<span class="token keyword">for</span><span class="token punctuation">(</span>i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i<span class="token operator">&lt;</span><span class="token number">5</span><span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		cout<span class="token operator">&lt;&lt;</span>a<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token operator">&lt;&lt;</span><span class="token string">"\t"</span><span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
	<span class="token keyword">return</span> <span class="token number">0</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

</code></pre>
<p>In python:</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">def</span> <span class="token function">bubbleSort</span><span class="token punctuation">(</span>alist<span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token keyword">for</span> passnum <span class="token keyword">in</span> <span class="token builtin">range</span><span class="token punctuation">(</span><span class="token builtin">len</span><span class="token punctuation">(</span>alist<span class="token punctuation">)</span><span class="token operator">-</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">0</span><span class="token punctuation">,</span><span class="token operator">-</span><span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token keyword">for</span> i <span class="token keyword">in</span> <span class="token builtin">range</span><span class="token punctuation">(</span>passnum<span class="token punctuation">)</span><span class="token punctuation">:</span>
            <span class="token keyword">if</span> alist<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token operator">&gt;</span>alist<span class="token punctuation">[</span>i<span class="token operator">+</span><span class="token number">1</span><span class="token punctuation">]</span><span class="token punctuation">:</span>
                temp <span class="token operator">=</span> alist<span class="token punctuation">[</span>i<span class="token punctuation">]</span>
                alist<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">=</span> alist<span class="token punctuation">)</span> alist<span class="token punctuation">[</span>i<span class="token operator">+</span><span class="token number">1</span><span class="token punctuation">]</span>
                alist<span class="token punctuation">[</span>i<span class="token operator">+</span><span class="token number">1</span><span class="token punctuation">]</span> <span class="token operator">=</span> temp

alist <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token number">54</span><span class="token punctuation">,</span><span class="token number">26</span><span class="token punctuation">,</span><span class="token number">93</span><span class="token punctuation">,</span><span class="token number">17</span><span class="token punctuation">,</span><span class="token number">77</span><span class="token punctuation">,</span><span class="token number">31</span><span class="token punctuation">,</span><span class="token number">44</span><span class="token punctuation">,</span><span class="token number">55</span><span class="token punctuation">,</span><span class="token number">20</span><span class="token punctuation">]</span>
bubbleSort<span class="token punctuation">(</span>alist<span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>alist<span class="token punctuation">)</span>

<span class="token comment">#another method</span>
<span class="token keyword">def</span> <span class="token function">bubble</span><span class="token punctuation">(</span>list_a<span class="token punctuation">)</span><span class="token punctuation">:</span>
	indexing_length <span class="token operator">=</span> <span class="token builtin">len</span><span class="token punctuation">(</span>list_a<span class="token punctuation">)</span> <span class="token operator">-</span> <span class="token number">1</span> 
	<span class="token builtin">sorted</span> <span class="token operator">=</span> <span class="token boolean">False</span> <span class="token comment">#Create variable of sorted and set it equal to false</span>
	
	<span class="token keyword">while</span> <span class="token operator">not</span> <span class="token builtin">sorted</span><span class="token punctuation">:</span> <span class="token comment">#Repeat until sorted = True</span>
		<span class="token builtin">sorted</span> <span class="token operator">=</span> <span class="token boolean">True</span> <span class="token comment"># Break the while loop whenever we have gone through all the values</span>
		<span class="token keyword">for</span> i <span class="token keyword">in</span> <span class="token builtin">range</span><span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">,</span> indexing_length<span class="token punctuation">)</span><span class="token punctuation">:</span> <span class="token comment"># For every value in the list</span>
			<span class="token keyword">if</span> list_a<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">&gt;</span> list_a<span class="token punctuation">[</span>i<span class="token operator">+</span><span class="token number">1</span><span class="token punctuation">]</span><span class="token punctuation">:</span> <span class="token comment">#if value in list is greater than value directly to the right of it,</span>
				<span class="token builtin">sorted</span> <span class="token operator">=</span> <span class="token boolean">False</span> <span class="token comment"># These values are unsorted</span>
				list_a<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">,</span> list_a<span class="token punctuation">[</span>i<span class="token operator">+</span><span class="token number">1</span><span class="token punctuation">]</span> <span class="token operator">=</span> list_a<span class="token punctuation">[</span>i<span class="token operator">+</span><span class="token number">1</span><span class="token punctuation">]</span><span class="token punctuation">,</span> list_a<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token comment">#Switch these values</span>
	<span class="token keyword">return</span> list_a <span class="token comment"># Return our list "unsorted_list" which is not sorted.</span>
</code></pre>

