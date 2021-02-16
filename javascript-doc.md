---


---

<h2 id="concepts">Concepts</h2>
<h3 id="push--pop">push &amp; pop:</h3>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">var</span> ourArray <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token string">"John"</span><span class="token punctuation">,</span> <span class="token number">23</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token punctuation">[</span><span class="token string">"Cat"</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">;</span>
ourArray<span class="token punctuation">.</span><span class="token function">push</span><span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token string">"Dog"</span><span class="token punctuation">,</span> <span class="token number">66</span><span class="token punctuation">]</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p><code>Output: [ [ 'John', 23 ], [ 'Cat', 2 ], [ 'Dog', 66 ] ]</code></p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">var</span> ourArray <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token string">"John"</span><span class="token punctuation">,</span> <span class="token number">23</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token punctuation">[</span><span class="token string">"Cat"</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">;</span>
ourArray<span class="token punctuation">.</span><span class="token function">pop</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p><code>Output: [ [ 'John', 23 ] ]</code></p>
<h3 id="shift--unshift">shift &amp; unshift:</h3>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">var</span> ourArray <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token string">"John"</span><span class="token punctuation">,</span> <span class="token number">23</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token punctuation">[</span><span class="token string">"Cat"</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">;</span>
ourArray<span class="token punctuation">.</span><span class="token function">shift</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p><code>Output: [ [ 'Cat', 2 ] ]</code></p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">var</span> ourArray <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token string">"John"</span><span class="token punctuation">,</span> <span class="token number">23</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token punctuation">[</span><span class="token string">"Cat"</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">;</span>
ourArray<span class="token punctuation">.</span><span class="token function">shift</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
ourArray<span class="token punctuation">.</span><span class="token function">unshift</span><span class="token punctuation">(</span><span class="token string">"Happy"</span><span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">// adding to first index</span>
</code></pre>
<p><code>Output: [ "Happy", [ 'Cat', 2 ] ]</code></p>
<h3 id="objects">Objects:</h3>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token comment">// create object</span>
<span class="token keyword">var</span> testObj <span class="token operator">=</span> <span class="token punctuation">{</span>
	<span class="token string">"hat"</span><span class="token punctuation">:</span> <span class="token string">"red"</span><span class="token punctuation">,</span>
	<span class="token string">"shirt"</span><span class="token punctuation">:</span> <span class="token string">"yellow"</span><span class="token punctuation">,</span>
	<span class="token string">"shoes"</span><span class="token punctuation">:</span> <span class="token string">"white"</span>
<span class="token punctuation">}</span><span class="token punctuation">;</span>
<span class="token comment">// Access objects' elements without space between object name</span>
<span class="token keyword">var</span> hatValue <span class="token operator">=</span> testObj<span class="token punctuation">.</span>hat<span class="token punctuation">;</span>

<span class="token comment">// Access objects' elements with space between object name</span>
<span class="token keyword">var</span> testObj <span class="token operator">=</span> <span class="token punctuation">{</span>
	<span class="token string">"hat cover"</span><span class="token punctuation">:</span> <span class="token string">"red"</span><span class="token punctuation">,</span>
	<span class="token string">"long shirt"</span><span class="token punctuation">:</span> <span class="token string">"yellow"</span>
<span class="token punctuation">}</span><span class="token punctuation">;</span>
<span class="token keyword">var</span> hatValue <span class="token operator">=</span> testObj<span class="token punctuation">[</span><span class="token string">"hat cover"</span><span class="token punctuation">]</span><span class="token punctuation">;</span>

<span class="token comment">// Adding new object attribute into object</span>
<span class="token keyword">var</span> ourDog <span class="token operator">=</span> <span class="token punctuation">{</span>
  <span class="token string">"name"</span><span class="token punctuation">:</span> <span class="token string">"Camper"</span><span class="token punctuation">,</span>
  <span class="token string">"legs"</span><span class="token punctuation">:</span> <span class="token number">4</span><span class="token punctuation">,</span>
  <span class="token string">"tails"</span><span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
  <span class="token string">"friends"</span><span class="token punctuation">:</span> <span class="token punctuation">[</span><span class="token string">"everything!"</span><span class="token punctuation">]</span>
<span class="token punctuation">}</span><span class="token punctuation">;</span>
ourDog<span class="token punctuation">.</span>bark <span class="token operator">=</span> <span class="token string">"bow-bow"</span><span class="token punctuation">;</span> 
<span class="token comment">// output: </span>
<span class="token punctuation">{</span>
  name<span class="token punctuation">:</span> <span class="token string">'Camper'</span><span class="token punctuation">,</span>
  legs<span class="token punctuation">:</span> <span class="token number">4</span><span class="token punctuation">,</span>
  tails<span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
  friends<span class="token punctuation">:</span> <span class="token punctuation">[</span> <span class="token string">'everything!'</span> <span class="token punctuation">]</span><span class="token punctuation">,</span>
  bark<span class="token punctuation">:</span> <span class="token string">'bow-bow'</span>
<span class="token punctuation">}</span>

<span class="token comment">// Deleting object attribut</span>
<span class="token keyword">delete</span> ourDog<span class="token punctuation">.</span>bark<span class="token punctuation">;</span>
<span class="token comment">// output: </span>
<span class="token punctuation">{</span>
  name<span class="token punctuation">:</span> <span class="token string">'Camper'</span><span class="token punctuation">,</span>
  legs<span class="token punctuation">:</span> <span class="token number">4</span><span class="token punctuation">,</span>
  tails<span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
  friends<span class="token punctuation">:</span> <span class="token punctuation">[</span> <span class="token string">'everything!'</span> <span class="token punctuation">]</span>
<span class="token punctuation">}</span>
</code></pre>

