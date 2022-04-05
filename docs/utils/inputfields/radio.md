<div class="section" id="radio">
<h1>radio<a class="headerlink" href="#radio" title="Lien permanent vers ce titre">¶</a></h1>
<dl class="py class">
<dt id="radio.Radio">
<em class="property"><span class="pre">class</span> </em><code class="sig-name descname"><span class="pre">Radio</span></code><span class="sig-paren">(</span><em class="sig-param"><span class="o"><span class="pre">**</span></span><span class="n"><span class="pre">kwargs</span></span></em><span class="sig-paren">)</span><a class="headerlink" href="#radio.Radio" title="Lien permanent vers cette définition">¶</a></dt>
<dd><dl class="py method">
<dt id="radio.Radio.set_items">
<code class="sig-name descname"><span class="pre">set_items</span></code><span class="sig-paren">(</span><em class="sig-param"><span class="n"><span class="pre">items</span></span></em><span class="sig-paren">)</span><a class="headerlink" href="#radio.Radio.set_items" title="Lien permanent vers cette définition">¶</a></dt>
<dd><p>Set the list of items used as choices.</p>
</dd></dl>

<dl class="py method">
<dt id="radio.Radio.set_sol">
<code class="sig-name descname"><span class="pre">set_sol</span></code><span class="sig-paren">(</span><em class="sig-param"><span class="n"><span class="pre">index</span></span></em><span class="sig-paren">)</span><a class="headerlink" href="#radio.Radio.set_sol" title="Lien permanent vers cette définition">¶</a></dt>
<dd><p>Set the solution item by giving its index in the list of items.</p>
</dd></dl>

<dl class="py method">
<dt id="radio.Radio.shuffle">
<code class="sig-name descname"><span class="pre">shuffle</span></code><span class="sig-paren">(</span><span class="sig-paren">)</span><a class="headerlink" href="#radio.Radio.shuffle" title="Lien permanent vers cette définition">¶</a></dt>
<dd><p>Shuffle the items.</p>
</dd></dl>

</dd></dl>

</div>

## Exemples

```py
>>> input = Radio()
>>> input.set_items(["Paris", "Rome", "Berlin"])
>>> input.set_sol(0)
>>> input.shuffle()
```
