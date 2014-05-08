<h1>
<a name="user-content-dable" class="anchor" href="#dable"><span class="octicon octicon-link"></span></a>Dable</h1>

<p>Dable (pronounced 'dabble') is a simple javascript table control with filtering, sorting, paging, styles, and more!</p>

<p>Dable is simple and elegant.  It has <strong>zero</strong> dependencies and works in IE8+.</p>

<h2>
<a name="user-content-also-found-on" class="anchor" href="#also-found-on"><span class="octicon octicon-link"></span></a>Also Found On</h2>

<p><strong>NuGet</strong>: <a href="https://www.nuget.org/packages/Dable/">https://www.nuget.org/packages/Dable/</a><br><strong>Chocolatey</strong>: <a href="https://chocolatey.org/packages/Dable/1.1.0">https://chocolatey.org/packages/Dable/1.1.0</a></p>

<h2>
<a name="user-content-how-to" class="anchor" href="#how-to"><span class="octicon octicon-link"></span></a>How To</h2>

<p>Initialize a new Dable with</p>

<div class="highlight highlight-javascript"><pre><span class="kd">var</span> <span class="nx">dable</span> <span class="o">=</span> <span class="k">new</span> <span class="nx">Dable</span><span class="p">();</span>
</pre></div>

<p>Build your Dable by giving it data and column names.</p>

<div class="highlight highlight-javascript"><pre><span class="kd">var</span> <span class="nx">data</span> <span class="o">=</span> <span class="p">[</span> <span class="p">[</span> <span class="mi">1</span><span class="p">,</span> <span class="mi">2</span> <span class="p">],</span> <span class="p">[</span> <span class="mi">3</span><span class="p">,</span> <span class="mi">4</span> <span class="p">]</span> <span class="p">];</span>
<span class="kd">var</span> <span class="nx">columns</span> <span class="o">=</span> <span class="p">[</span> <span class="s1">'Odd'</span><span class="p">,</span> <span class="s1">'Even'</span> <span class="p">];</span>

<span class="nx">dable</span><span class="p">.</span><span class="nx">SetDataAsRows</span><span class="p">(</span><span class="nx">data</span><span class="p">);</span>      <span class="c1">// We can import data as rows or columns for flexibility</span>
<span class="nx">dable</span><span class="p">.</span><span class="nx">SetColumnNames</span><span class="p">(</span><span class="nx">columns</span><span class="p">);</span>  <span class="c1">// Because the data is raw, we need to name our columns</span>
</pre></div>

<p>If you want to style your Dable, you can use custom styling with easy to remember classes and IDs.
Or you can just select JQueryUI or Bootstrap for preconfigured styles.</p>

<div class="highlight highlight-javascript"><pre><span class="nx">dable</span><span class="p">.</span><span class="nx">style</span> <span class="o">=</span> <span class="s2">"JqueryUI"</span><span class="p">;</span>   <span class="c1">// Don't worry about uppercase/lowercase</span>
</pre></div>

<p>Dable is pure javascript, so you don't have to add a CSS file to your project.  However, if you use a custom style, make sure you include the relevant stylesheet.</p>

<p>Creating your Dable is as simple as using the id of a div from your page and calling</p>

<div class="highlight highlight-javascript"><pre><span class="nx">dable</span><span class="p">.</span><span class="nx">BuildAll</span><span class="p">(</span><span class="nx">divId</span><span class="p">);</span>
</pre></div>

<p>Or, if you prefer HTML to Javascript, build your table in HTML, and then create your Dable in one step.</p>

<div class="highlight highlight-html"><pre><span class="nt">&lt;div</span> <span class="na">id=</span><span class="s">"TableDable"</span><span class="nt">&gt;</span>
    <span class="nt">&lt;table&gt;</span>
        <span class="nt">&lt;thead&gt;</span>
            <span class="nt">&lt;tr&gt;</span>
                <span class="nt">&lt;th&gt;</span>Odd<span class="nt">&lt;/th&gt;</span>
                <span class="nt">&lt;th&gt;</span>Even<span class="nt">&lt;/th&gt;</span>
            <span class="nt">&lt;/tr&gt;</span>
        <span class="nt">&lt;/thead&gt;</span>
        <span class="nt">&lt;tbody&gt;</span>
            <span class="nt">&lt;tr&gt;</span>
                <span class="nt">&lt;td&gt;</span>1<span class="nt">&lt;/td&gt;</span>
                <span class="nt">&lt;td&gt;</span>2<span class="nt">&lt;/td&gt;</span>
            <span class="nt">&lt;/tr&gt;</span>
            <span class="nt">&lt;tr&gt;</span>
                <span class="nt">&lt;td&gt;</span>3<span class="nt">&lt;/td&gt;</span>
                <span class="nt">&lt;td&gt;</span>4<span class="nt">&lt;/td&gt;</span>
            <span class="nt">&lt;/tr&gt;</span>
        <span class="nt">&lt;/tbody&gt;</span>
    <span class="nt">&lt;/table&gt;</span>
<span class="nt">&lt;/div&gt;</span>
<span class="nt">&lt;script </span><span class="na">type=</span><span class="s">"text/javascript"</span><span class="nt">&gt;</span>
    <span class="kd">var</span> <span class="nx">dable</span> <span class="o">=</span> <span class="k">new</span> <span class="nx">Dable</span><span class="p">(</span><span class="s2">"TableDable"</span><span class="p">);</span>
<span class="nt">&lt;/script&gt;</span>
</pre></div>

<p><strong>Everything in Dable is designed to be modifiable by you.</strong></p>

<p>The Search is an array of callbacks, so you can add your own with a simple command.</p>

<div class="highlight highlight-javascript"><pre><span class="nx">dable</span><span class="p">.</span><span class="nx">filters</span><span class="p">.</span><span class="nx">push</span><span class="p">(</span><span class="kd">function</span> <span class="p">(</span><span class="nx">searchText</span><span class="p">,</span> <span class="nx">cellValue</span><span class="p">)</span> <span class="p">{</span>
    <span class="c1">//this is a custom filter</span>
<span class="p">});</span>
</pre></div>

<p>Because it's a simple array, you can wipe out the existing filters altogether if you don't like them.
Your columns are a simple object array.  Each object has a <code>Tag</code>, a <code>FriendlyName</code>, and can be provided with <code>CustomRendering</code> and <code>CustomSortFunc</code> callbacks</p>

<div class="highlight highlight-javascript"><pre><span class="p">{</span> <span class="nx">Tag</span><span class="p">,</span> <span class="nx">FriendlyName</span><span class="p">,</span> <span class="nx">CustomSortFunc</span><span class="p">,</span> <span class="nx">CustomRendering</span> <span class="p">}</span>
</pre></div>

<p>These callbacks are simple to use too.  When you want to render something uniquely, just return the text to render and it'll be stuck in the cell.</p>

<div class="highlight highlight-javascript"><pre><span class="nx">dable</span><span class="p">.</span><span class="nx">columnData</span><span class="p">[</span><span class="mi">0</span><span class="p">].</span><span class="nx">CustomRendering</span> <span class="o">=</span> <span class="kd">function</span> <span class="p">(</span><span class="nx">cellValue</span><span class="p">)</span> <span class="p">{</span>
    <span class="k">return</span> <span class="s1">'&lt;a target="_blank" href="/?cell='</span> <span class="o">+</span> <span class="nx">cellValue</span> <span class="o">+</span> <span class="s1">'"&gt;'</span> <span class="o">+</span> <span class="nx">cellValue</span> <span class="o">+</span> <span class="s1">'&lt;/a&gt;'</span><span class="p">;</span>
<span class="p">}</span>
</pre></div>

<p>When you want to sort something uniquely, just return an array of the rows to present in whatever order you want.</p>

<div class="highlight highlight-javascript"><pre><span class="nx">dable</span><span class="p">.</span><span class="nx">columnData</span><span class="p">[</span><span class="mi">1</span><span class="p">].</span><span class="nx">CustomSortFunc</span> <span class="o">=</span> <span class="kd">function</span> <span class="p">(</span><span class="nx">columnIndex</span><span class="p">,</span> <span class="nx">ascending</span><span class="p">,</span> <span class="nx">currentRowObjects</span><span class="p">)</span> <span class="p">{</span>
    <span class="k">return</span> <span class="nx">currentRowObjects</span><span class="p">.</span><span class="nx">reverse</span><span class="p">();</span>
<span class="p">}</span>
</pre></div>

<p>The <code>CustomSortFunc</code> property also allows you to keep a column from sorting.  Just set it to <code>false</code>.</p>

<div class="highlight highlight-javascript"><pre><span class="nx">dable</span><span class="p">.</span><span class="nx">columnData</span><span class="p">[</span><span class="mi">2</span><span class="p">].</span><span class="nx">CustomSortFunc</span> <span class="o">=</span> <span class="kc">false</span><span class="p">;</span>
</pre></div>

<p>What about printing?  If your table is paged, you need to be able to output all the rows to print!
Here's a sample of how to do this extremely complex Dable procedure.</p>

<div class="highlight highlight-javascript"><pre><span class="nx">dable</span><span class="p">.</span><span class="nx">pageNumber</span> <span class="o">=</span> <span class="mi">0</span><span class="p">;</span>               <span class="c1">// Go back to the first page</span>
<span class="nx">dable</span><span class="p">.</span><span class="nx">pageSize</span> <span class="o">=</span> <span class="nx">dable</span><span class="p">.</span><span class="nx">rows</span><span class="p">.</span><span class="nx">length</span><span class="p">;</span> <span class="c1">// Change the page size to the whole table size</span>
<span class="nx">dable</span><span class="p">.</span><span class="nx">UpdateDisplayedRows</span><span class="p">();</span>        <span class="c1">// Update the table</span>
<span class="nx">dable</span><span class="p">.</span><span class="nx">UpdateStyle</span><span class="p">();</span>                <span class="c1">// Reapply our styles</span>
</pre></div>

<p>Every function inside of Dable is accessible, down to the initial rendering functions!</p>

<p>For more examples, check out the site! <a href="http://deltreey.github.io/Dable/">http://deltreey.github.io/Dable/</a></p>

<h2>
<a name="user-content-breaking-changes" class="anchor" href="#breaking-changes"><span class="octicon octicon-link"></span></a>Breaking Changes</h2>

<p><code>1.0 - 1.1:</code> Dable custom sort functions now use rowObjects instead of rows.  rowObjects have the <code>Row</code> property which contains the row as it existed before but also includes the <code>RowNumber</code> property which makes things like delete buttons easier to implement.</p>