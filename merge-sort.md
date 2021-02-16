---


---

<h2 id="merge-sort">Merge Sort</h2>
<h3 id="description">Description</h3>
<p>In this technique, we divide the list first into equal halves. Then we perform merge sort technique on these lists independently so that both the lists are sorted. Finally, we merge both the lists to get a complete sorted list.</p>
<h3 id="runtime">Runtime</h3>

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
<td><span class="katex--inline"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi>θ</mi><mo stretchy="false">(</mo><mi>n</mi><mi>l</mi><mi>o</mi><mi>g</mi><mo stretchy="false">(</mo><mi>n</mi><mo stretchy="false">)</mo><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">θ(n log(n))</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathdefault" style="margin-right: 0.02778em;">θ</span><span class="mopen">(</span><span class="mord mathdefault">n</span><span class="mord mathdefault" style="margin-right: 0.01968em;">l</span><span class="mord mathdefault">o</span><span class="mord mathdefault" style="margin-right: 0.03588em;">g</span><span class="mopen">(</span><span class="mord mathdefault">n</span><span class="mclose">)</span><span class="mclose">)</span></span></span></span></span></td>
<td><span class="katex--inline"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi mathvariant="normal">Ω</mi><mo stretchy="false">(</mo><mi>n</mi><mi>l</mi><mi>o</mi><mi>g</mi><mo stretchy="false">(</mo><mi>n</mi><mo stretchy="false">)</mo><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">Ω(n log(n))</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord">Ω</span><span class="mopen">(</span><span class="mord mathdefault">n</span><span class="mord mathdefault" style="margin-right: 0.01968em;">l</span><span class="mord mathdefault">o</span><span class="mord mathdefault" style="margin-right: 0.03588em;">g</span><span class="mopen">(</span><span class="mord mathdefault">n</span><span class="mclose">)</span><span class="mclose">)</span></span></span></span></span></td>
</tr>
</tbody>
</table><h3 id="diagram">Diagram</h3>
<p><img src="https://www.softwaretestinghelp.com/wp-content/qa/uploads/2019/06/Merge-Sort.png" alt="1"></p>
<h3 id="code">Code</h3>
<p><a href="https://www.programiz.com/dsa/merge-sort">Explaination for each step</a><br>
In C++:</p>
<pre class=" language-c"><code class="prism ++ language-c"><span class="token comment">// Merge sort in C++</span>

<span class="token macro property">#<span class="token directive keyword">include</span> <span class="token string">&lt;iostream&gt;</span></span>
using namespace std<span class="token punctuation">;</span>

<span class="token comment">// Merge two subarrays L and M into arr</span>
<span class="token keyword">void</span> <span class="token function">merge</span><span class="token punctuation">(</span><span class="token keyword">int</span> arr<span class="token punctuation">[</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token keyword">int</span> p<span class="token punctuation">,</span> <span class="token keyword">int</span> q<span class="token punctuation">,</span> <span class="token keyword">int</span> r<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  
  <span class="token comment">// Create L ← A[p..q] and M ← A[q+1..r]</span>
  <span class="token keyword">int</span> n1 <span class="token operator">=</span> q <span class="token operator">-</span> p <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">;</span>
  <span class="token keyword">int</span> n2 <span class="token operator">=</span> r <span class="token operator">-</span> q<span class="token punctuation">;</span>

  <span class="token keyword">int</span> L<span class="token punctuation">[</span>n1<span class="token punctuation">]</span><span class="token punctuation">,</span> M<span class="token punctuation">[</span>n2<span class="token punctuation">]</span><span class="token punctuation">;</span>

  <span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> n1<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span>
    L<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">=</span> arr<span class="token punctuation">[</span>p <span class="token operator">+</span> i<span class="token punctuation">]</span><span class="token punctuation">;</span>
  <span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> j <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> j <span class="token operator">&lt;</span> n2<span class="token punctuation">;</span> j<span class="token operator">++</span><span class="token punctuation">)</span>
    M<span class="token punctuation">[</span>j<span class="token punctuation">]</span> <span class="token operator">=</span> arr<span class="token punctuation">[</span>q <span class="token operator">+</span> <span class="token number">1</span> <span class="token operator">+</span> j<span class="token punctuation">]</span><span class="token punctuation">;</span>

  <span class="token comment">// Maintain current index of sub-arrays and main array</span>
  <span class="token keyword">int</span> i<span class="token punctuation">,</span> j<span class="token punctuation">,</span> k<span class="token punctuation">;</span>
  i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span>
  j <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span>
  k <span class="token operator">=</span> p<span class="token punctuation">;</span>

  <span class="token comment">// Until we reach either end of either L or M, pick larger among</span>
  <span class="token comment">// elements L and M and place them in the correct position at A[p..r]</span>
  <span class="token keyword">while</span> <span class="token punctuation">(</span>i <span class="token operator">&lt;</span> n1 <span class="token operator">&amp;&amp;</span> j <span class="token operator">&lt;</span> n2<span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">if</span> <span class="token punctuation">(</span>L<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">&lt;=</span> M<span class="token punctuation">[</span>j<span class="token punctuation">]</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
      arr<span class="token punctuation">[</span>k<span class="token punctuation">]</span> <span class="token operator">=</span> L<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">;</span>
      i<span class="token operator">++</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span> <span class="token keyword">else</span> <span class="token punctuation">{</span>
      arr<span class="token punctuation">[</span>k<span class="token punctuation">]</span> <span class="token operator">=</span> M<span class="token punctuation">[</span>j<span class="token punctuation">]</span><span class="token punctuation">;</span>
      j<span class="token operator">++</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span>
    k<span class="token operator">++</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>

  <span class="token comment">// When we run out of elements in either L or M,</span>
  <span class="token comment">// pick up the remaining elements and put in A[p..r]</span>
  <span class="token keyword">while</span> <span class="token punctuation">(</span>i <span class="token operator">&lt;</span> n1<span class="token punctuation">)</span> <span class="token punctuation">{</span>
    arr<span class="token punctuation">[</span>k<span class="token punctuation">]</span> <span class="token operator">=</span> L<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">;</span>
    i<span class="token operator">++</span><span class="token punctuation">;</span>
    k<span class="token operator">++</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>

  <span class="token keyword">while</span> <span class="token punctuation">(</span>j <span class="token operator">&lt;</span> n2<span class="token punctuation">)</span> <span class="token punctuation">{</span>
    arr<span class="token punctuation">[</span>k<span class="token punctuation">]</span> <span class="token operator">=</span> M<span class="token punctuation">[</span>j<span class="token punctuation">]</span><span class="token punctuation">;</span>
    j<span class="token operator">++</span><span class="token punctuation">;</span>
    k<span class="token operator">++</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span>

<span class="token comment">// Divide the array into two subarrays, sort them and merge them</span>
<span class="token keyword">void</span> <span class="token function">mergeSort</span><span class="token punctuation">(</span><span class="token keyword">int</span> arr<span class="token punctuation">[</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token keyword">int</span> l<span class="token punctuation">,</span> <span class="token keyword">int</span> r<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">if</span> <span class="token punctuation">(</span>l <span class="token operator">&lt;</span> r<span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token comment">// m is the point where the array is divided into two subarrays</span>
    <span class="token keyword">int</span> m <span class="token operator">=</span> l <span class="token operator">+</span> <span class="token punctuation">(</span>r <span class="token operator">-</span> l<span class="token punctuation">)</span> <span class="token operator">/</span> <span class="token number">2</span><span class="token punctuation">;</span>

    <span class="token function">mergeSort</span><span class="token punctuation">(</span>arr<span class="token punctuation">,</span> l<span class="token punctuation">,</span> m<span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token function">mergeSort</span><span class="token punctuation">(</span>arr<span class="token punctuation">,</span> m <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">,</span> r<span class="token punctuation">)</span><span class="token punctuation">;</span>

    <span class="token comment">// Merge the sorted subarrays</span>
    <span class="token function">merge</span><span class="token punctuation">(</span>arr<span class="token punctuation">,</span> l<span class="token punctuation">,</span> m<span class="token punctuation">,</span> r<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span>

<span class="token comment">// Print the array</span>
<span class="token keyword">void</span> <span class="token function">printArray</span><span class="token punctuation">(</span><span class="token keyword">int</span> arr<span class="token punctuation">[</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token keyword">int</span> size<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> size<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span>
    cout <span class="token operator">&lt;&lt;</span> arr<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">&lt;&lt;</span> <span class="token string">" "</span><span class="token punctuation">;</span>
  cout <span class="token operator">&lt;&lt;</span> endl<span class="token punctuation">;</span>
<span class="token punctuation">}</span>

<span class="token comment">// Driver program</span>
<span class="token keyword">int</span> <span class="token function">main</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">int</span> arr<span class="token punctuation">[</span><span class="token punctuation">]</span> <span class="token operator">=</span> <span class="token punctuation">{</span><span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">12</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">}</span><span class="token punctuation">;</span>
  <span class="token keyword">int</span> size <span class="token operator">=</span> <span class="token keyword">sizeof</span><span class="token punctuation">(</span>arr<span class="token punctuation">)</span> <span class="token operator">/</span> <span class="token keyword">sizeof</span><span class="token punctuation">(</span>arr<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

  <span class="token function">mergeSort</span><span class="token punctuation">(</span>arr<span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> size <span class="token operator">-</span> <span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

  cout <span class="token operator">&lt;&lt;</span> <span class="token string">"Sorted array: \n"</span><span class="token punctuation">;</span>
  <span class="token function">printArray</span><span class="token punctuation">(</span>arr<span class="token punctuation">,</span> size<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token keyword">return</span> <span class="token number">0</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>In python:</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">def</span> <span class="token function">mergeSort</span><span class="token punctuation">(</span>array<span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token keyword">if</span> <span class="token builtin">len</span><span class="token punctuation">(</span>array<span class="token punctuation">)</span> <span class="token operator">&gt;</span> <span class="token number">1</span><span class="token punctuation">:</span>

        <span class="token comment">#  r is the point where the array is divided into two subarrays</span>
        r <span class="token operator">=</span> <span class="token builtin">len</span><span class="token punctuation">(</span>array<span class="token punctuation">)</span><span class="token operator">//</span><span class="token number">2</span>
        L <span class="token operator">=</span> array<span class="token punctuation">[</span><span class="token punctuation">:</span>r<span class="token punctuation">]</span>
        M <span class="token operator">=</span> array<span class="token punctuation">[</span>r<span class="token punctuation">:</span><span class="token punctuation">]</span>

        <span class="token comment"># Sort the two halves</span>
        mergeSort<span class="token punctuation">(</span>L<span class="token punctuation">)</span>
        mergeSort<span class="token punctuation">(</span>M<span class="token punctuation">)</span>

        i <span class="token operator">=</span> j <span class="token operator">=</span> k <span class="token operator">=</span> <span class="token number">0</span>

        <span class="token comment"># Until we reach either end of either L or M, pick larger among</span>
        <span class="token comment"># elements L and M and place them in the correct position at A[p..r]</span>
        <span class="token keyword">while</span> i <span class="token operator">&lt;</span> <span class="token builtin">len</span><span class="token punctuation">(</span>L<span class="token punctuation">)</span> <span class="token operator">and</span> j <span class="token operator">&lt;</span> <span class="token builtin">len</span><span class="token punctuation">(</span>M<span class="token punctuation">)</span><span class="token punctuation">:</span>
            <span class="token keyword">if</span> L<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">&lt;</span> M<span class="token punctuation">[</span>j<span class="token punctuation">]</span><span class="token punctuation">:</span>
                array<span class="token punctuation">[</span>k<span class="token punctuation">]</span> <span class="token operator">=</span> L<span class="token punctuation">[</span>i<span class="token punctuation">]</span>
                i <span class="token operator">+=</span> <span class="token number">1</span>
            <span class="token keyword">else</span><span class="token punctuation">:</span>
                array<span class="token punctuation">[</span>k<span class="token punctuation">]</span> <span class="token operator">=</span> M<span class="token punctuation">[</span>j<span class="token punctuation">]</span>
                j <span class="token operator">+=</span> <span class="token number">1</span>
            k <span class="token operator">+=</span> <span class="token number">1</span>

        <span class="token comment"># When we run out of elements in either L or M,</span>
        <span class="token comment"># pick up the remaining elements and put in A[p..r]</span>
        <span class="token keyword">while</span> i <span class="token operator">&lt;</span> <span class="token builtin">len</span><span class="token punctuation">(</span>L<span class="token punctuation">)</span><span class="token punctuation">:</span>
            array<span class="token punctuation">[</span>k<span class="token punctuation">]</span> <span class="token operator">=</span> L<span class="token punctuation">[</span>i<span class="token punctuation">]</span>
            i <span class="token operator">+=</span> <span class="token number">1</span>
            k <span class="token operator">+=</span> <span class="token number">1</span>

        <span class="token keyword">while</span> j <span class="token operator">&lt;</span> <span class="token builtin">len</span><span class="token punctuation">(</span>M<span class="token punctuation">)</span><span class="token punctuation">:</span>
            array<span class="token punctuation">[</span>k<span class="token punctuation">]</span> <span class="token operator">=</span> M<span class="token punctuation">[</span>j<span class="token punctuation">]</span>
            j <span class="token operator">+=</span> <span class="token number">1</span>
            k <span class="token operator">+=</span> <span class="token number">1</span>


<span class="token comment"># Print the array</span>
<span class="token keyword">def</span> <span class="token function">printList</span><span class="token punctuation">(</span>array<span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token keyword">for</span> i <span class="token keyword">in</span> <span class="token builtin">range</span><span class="token punctuation">(</span><span class="token builtin">len</span><span class="token punctuation">(</span>array<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token keyword">print</span><span class="token punctuation">(</span>array<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">,</span> end<span class="token operator">=</span><span class="token string">" "</span><span class="token punctuation">)</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token punctuation">)</span>


<span class="token comment"># Driver program</span>
<span class="token keyword">if</span> __name__ <span class="token operator">==</span> <span class="token string">'__main__'</span><span class="token punctuation">:</span>
    array <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">12</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">]</span>

    mergeSort<span class="token punctuation">(</span>array<span class="token punctuation">)</span>

    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Sorted array is: "</span><span class="token punctuation">)</span>
    printList<span class="token punctuation">(</span>array<span class="token punctuation">)</span>
</code></pre>

