
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"><html><head><META http-equiv="Content-Type" content="text/html; charset=utf-8"><style></style></head><body>﻿<u></u><div>















    




    
    
    
    


<div class="m_jp-Cell m_jp-MarkdownCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea"><div class="m_jp-InputPrompt m_jp-InputArea-prompt">
</div><div class="m_jp-RenderedHTMLCommon m_jp-RenderedMarkdown m_jp-MarkdownOutput">
<h1>Science Fair 2023<a rel="noopener noreferrer" class="m_anchor-link" href="#m__Science-Fair-2023">¶</a></h1><h2>Making an AI Model That Predicts Earthquakes&#39; Magnitudes<a rel="noopener noreferrer" class="m_anchor-link" href="#m__Making-an-AI-Model-That-Predicts-Earthquakes&#39;-Magnitudes">¶</a></h2><p><em>Nadia Radwan - WWSEF</em></p>

</div>
</div>
</div>
</div>
<div class="m_jp-Cell m_jp-MarkdownCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea"><div class="m_jp-InputPrompt m_jp-InputArea-prompt">
</div><div class="m_jp-RenderedHTMLCommon m_jp-RenderedMarkdown m_jp-MarkdownOutput">
<p><img src="https://ci3.googleusercontent.com/proxy/-yRfF__6QUgKU0fUCjE6NvStoIE1eV13ssxrvE75-TW-K3r0JTcFPEAG42xLOYEtHq1qqbJWa35bYymlR2X-azZbWGEslvFRdGUfVC7H__nnTKBHorHLb4G82Gkd8l9UW6Skxoe_R_cahrA=s0-d-e1-ft#https://th.bing.com/th/id/OIP.8DArMdLNu0s5X6iuShmAhQHaFA?w=267&amp;h=181&amp;c=7&amp;r=0&amp;o=5&amp;pid=1.7" alt="Wikimedia Commons/&gt;"></p>

</div>
</div>
</div>
</div>
<div class="m_jp-Cell m_jp-MarkdownCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea"><div class="m_jp-InputPrompt m_jp-InputArea-prompt">
</div><div class="m_jp-RenderedHTMLCommon m_jp-RenderedMarkdown m_jp-MarkdownOutput">
<hr>
<h1>Part 1<a rel="noopener noreferrer" class="m_anchor-link" href="#m__Part-1">¶</a></h1><h2>Making Predictions<a rel="noopener noreferrer" class="m_anchor-link" href="#m__Making-Predictions">¶</a></h2>
</div>
</div>
</div>
</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell m_jp-mod-noOutputs">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [165]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_kn">import</span> <span class="m_nn">numpy</span> <span class="m_k">as</span> <span class="m_nn">np</span>
<span class="m_kn">import</span> <span class="m_nn">pandas</span> <span class="m_k">as</span> <span class="m_nn">pd</span>
<span class="m_kn">import</span> <span class="m_nn">matplotlib.pyplot</span> <span class="m_k">as</span> <span class="m_nn">plt</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [6]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">data</span> <span class="m_o">=</span> <span class="m_n">pd</span><span class="m_o">.</span><span class="m_n">read_csv</span><span class="m_p">(</span><span class="m_s2">&quot;database.csv&quot;</span><span class="m_p">)</span>
<span class="m_n">data</span><span class="m_o">.</span><span class="m_n">head</span><span class="m_p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child m_jp-OutputArea-executeResult">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt">Out[6]:</div>



<div class="m_jp-RenderedHTMLCommon m_jp-RenderedHTML m_jp-OutputArea-output m_jp-OutputArea-executeResult">
<div>

<table border="1" class="m_dataframe">
  <thead>
    <tr style="text-align:right">
      <th></th>
      <th>Date</th>
      <th>Time</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Type</th>
      <th>Depth</th>
      <th>Depth Error</th>
      <th>Depth Seismic Stations</th>
      <th>Magnitude</th>
      <th>Magnitude Type</th>
      <th>...</th>
      <th>Magnitude Seismic Stations</th>
      <th>Azimuthal Gap</th>
      <th>Horizontal Distance</th>
      <th>Horizontal Error</th>
      <th>Root Mean Square</th>
      <th>ID</th>
      <th>Source</th>
      <th>Location Source</th>
      <th>Magnitude Source</th>
      <th>Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>01/02/1965</td>
      <td>13:44:18</td>
      <td>19.246</td>
      <td>145.616</td>
      <td>Earthquake</td>
      <td>131.6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>MW</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>ISCGEM860706</td>
      <td>ISCGEM</td>
      <td>ISCGEM</td>
      <td>ISCGEM</td>
      <td>Automatic</td>
    </tr>
    <tr>
      <th>1</th>
      <td>01/04/1965</td>
      <td>11:29:49</td>
      <td>1.863</td>
      <td>127.352</td>
      <td>Earthquake</td>
      <td>80.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.8</td>
      <td>MW</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>ISCGEM860737</td>
      <td>ISCGEM</td>
      <td>ISCGEM</td>
      <td>ISCGEM</td>
      <td>Automatic</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01/05/1965</td>
      <td>18:05:58</td>
      <td>-20.579</td>
      <td>-173.972</td>
      <td>Earthquake</td>
      <td>20.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.2</td>
      <td>MW</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>ISCGEM860762</td>
      <td>ISCGEM</td>
      <td>ISCGEM</td>
      <td>ISCGEM</td>
      <td>Automatic</td>
    </tr>
    <tr>
      <th>3</th>
      <td>01/08/1965</td>
      <td>18:49:43</td>
      <td>-59.076</td>
      <td>-23.557</td>
      <td>Earthquake</td>
      <td>15.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.8</td>
      <td>MW</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>ISCGEM860856</td>
      <td>ISCGEM</td>
      <td>ISCGEM</td>
      <td>ISCGEM</td>
      <td>Automatic</td>
    </tr>
    <tr>
      <th>4</th>
      <td>01/09/1965</td>
      <td>13:32:50</td>
      <td>11.938</td>
      <td>126.427</td>
      <td>Earthquake</td>
      <td>15.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.8</td>
      <td>MW</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>ISCGEM860890</td>
      <td>ISCGEM</td>
      <td>ISCGEM</td>
      <td>ISCGEM</td>
      <td>Automatic</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 21 columns</p>
</div>
</div>

</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [7]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">data</span><span class="m_o">.</span><span class="m_n">columns</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child m_jp-OutputArea-executeResult">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt">Out[7]:</div>




<div class="m_jp-RenderedText m_jp-OutputArea-output m_jp-OutputArea-executeResult">
<pre>Index([&#39;Date&#39;, &#39;Time&#39;, &#39;Latitude&#39;, &#39;Longitude&#39;, &#39;Type&#39;, &#39;Depth&#39;, &#39;Depth Error&#39;,
       &#39;Depth Seismic Stations&#39;, &#39;Magnitude&#39;, &#39;Magnitude Type&#39;,
       &#39;Magnitude Error&#39;, &#39;Magnitude Seismic Stations&#39;, &#39;Azimuthal Gap&#39;,
       &#39;Horizontal Distance&#39;, &#39;Horizontal Error&#39;, &#39;Root Mean Square&#39;, &#39;ID&#39;,
       &#39;Source&#39;, &#39;Location Source&#39;, &#39;Magnitude Source&#39;, &#39;Status&#39;],
      dtype=&#39;object&#39;)</pre>
</div>

</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [8]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">df</span> <span class="m_o">=</span> <span class="m_n">data</span><span class="m_p">[[</span><span class="m_s1">&#39;Date&#39;</span><span class="m_p">,</span> <span class="m_s1">&#39;Time&#39;</span><span class="m_p">,</span> <span class="m_s1">&#39;Latitude&#39;</span><span class="m_p">,</span> <span class="m_s1">&#39;Longitude&#39;</span><span class="m_p">,</span> <span class="m_s1">&#39;Depth&#39;</span><span class="m_p">,</span> <span class="m_s1">&#39;Magnitude&#39;</span><span class="m_p">]]</span>
<span class="m_n">df</span><span class="m_o">.</span><span class="m_n">head</span><span class="m_p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child m_jp-OutputArea-executeResult">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt">Out[8]:</div>



<div class="m_jp-RenderedHTMLCommon m_jp-RenderedHTML m_jp-OutputArea-output m_jp-OutputArea-executeResult">
<div>

<table border="1" class="m_dataframe">
  <thead>
    <tr style="text-align:right">
      <th></th>
      <th>Date</th>
      <th>Time</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Depth</th>
      <th>Magnitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>01/02/1965</td>
      <td>13:44:18</td>
      <td>19.246</td>
      <td>145.616</td>
      <td>131.6</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>01/04/1965</td>
      <td>11:29:49</td>
      <td>1.863</td>
      <td>127.352</td>
      <td>80.0</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01/05/1965</td>
      <td>18:05:58</td>
      <td>-20.579</td>
      <td>-173.972</td>
      <td>20.0</td>
      <td>6.2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>01/08/1965</td>
      <td>18:49:43</td>
      <td>-59.076</td>
      <td>-23.557</td>
      <td>15.0</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>4</th>
      <td>01/09/1965</td>
      <td>13:32:50</td>
      <td>11.938</td>
      <td>126.427</td>
      <td>15.0</td>
      <td>5.8</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [9]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">df</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child m_jp-OutputArea-executeResult">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt">Out[9]:</div>



<div class="m_jp-RenderedHTMLCommon m_jp-RenderedHTML m_jp-OutputArea-output m_jp-OutputArea-executeResult">
<div>

<table border="1" class="m_dataframe">
  <thead>
    <tr style="text-align:right">
      <th></th>
      <th>Date</th>
      <th>Time</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Depth</th>
      <th>Magnitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>01/02/1965</td>
      <td>13:44:18</td>
      <td>19.2460</td>
      <td>145.6160</td>
      <td>131.60</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>01/04/1965</td>
      <td>11:29:49</td>
      <td>1.8630</td>
      <td>127.3520</td>
      <td>80.00</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01/05/1965</td>
      <td>18:05:58</td>
      <td>-20.5790</td>
      <td>-173.9720</td>
      <td>20.00</td>
      <td>6.2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>01/08/1965</td>
      <td>18:49:43</td>
      <td>-59.0760</td>
      <td>-23.5570</td>
      <td>15.00</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>4</th>
      <td>01/09/1965</td>
      <td>13:32:50</td>
      <td>11.9380</td>
      <td>126.4270</td>
      <td>15.00</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>23407</th>
      <td>12/28/2016</td>
      <td>08:22:12</td>
      <td>38.3917</td>
      <td>-118.8941</td>
      <td>12.30</td>
      <td>5.6</td>
    </tr>
    <tr>
      <th>23408</th>
      <td>12/28/2016</td>
      <td>09:13:47</td>
      <td>38.3777</td>
      <td>-118.8957</td>
      <td>8.80</td>
      <td>5.5</td>
    </tr>
    <tr>
      <th>23409</th>
      <td>12/28/2016</td>
      <td>12:38:51</td>
      <td>36.9179</td>
      <td>140.4262</td>
      <td>10.00</td>
      <td>5.9</td>
    </tr>
    <tr>
      <th>23410</th>
      <td>12/29/2016</td>
      <td>22:30:19</td>
      <td>-9.0283</td>
      <td>118.6639</td>
      <td>79.00</td>
      <td>6.3</td>
    </tr>
    <tr>
      <th>23411</th>
      <td>12/30/2016</td>
      <td>20:08:28</td>
      <td>37.3973</td>
      <td>141.4103</td>
      <td>11.94</td>
      <td>5.5</td>
    </tr>
  </tbody>
</table>
<p>23412 rows × 6 columns</p>
</div>
</div>

</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [10]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">df</span><span class="m_p">[</span><span class="m_s1">&#39;timestamp&#39;</span><span class="m_p">]</span> <span class="m_o">=</span> <span class="m_n">df</span><span class="m_p">[</span><span class="m_s1">&#39;Date&#39;</span><span class="m_p">]</span> <span class="m_o">+</span> <span class="m_s1">&#39; &#39;</span> <span class="m_o">+</span> <span class="m_n">df</span><span class="m_p">[</span><span class="m_s1">&#39;Time&#39;</span><span class="m_p">]</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>


<div class="m_jp-RenderedText m_jp-OutputArea-output">
<pre>C:\Users\abeer\AppData\Local\<wbr>Temp\ipykernel_17132\<wbr>3303721065.py:1: SettingWithCopyWarning: 
A value is trying to be set on a copy of a slice from a DataFrame.
Try using .loc[row_indexer,col_indexer] = value instead

See the caveats in the documentation: <a href="https://www.google.com/url?q=https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html%23returning-a-view-versus-a-copy&amp;source=gmail-html&amp;ust=1690055563884000&amp;usg=AOvVaw2W3vwM2RSZN0p2ZLwrWk2n" target="_blank" rel="noreferrer">https://pandas.pydata.org/<wbr>pandas-docs/stable/user_guide/<wbr>indexing.html#returning-a-<wbr>view-versus-a-copy</a>
  df[&#39;timestamp&#39;] = df[&#39;Date&#39;] + &#39; &#39; + df[&#39;Time&#39;]
</pre>
</div>
</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [11]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">df</span><span class="m_p">[</span><span class="m_s1">&#39;timestamp&#39;</span><span class="m_p">]</span> <span class="m_o">=</span> <span class="m_n">pd</span><span class="m_o">.</span><span class="m_n">to_datetime</span><span class="m_p">(</span><span class="m_n">df</span><span class="m_p">[</span><span class="m_s1">&#39;timestamp&#39;</span><span class="m_p">]<wbr>,</span><span class="m_n">errors</span><span class="m_o">=</span><span class="m_s1">&#39;coerce&#39;</span> <span class="m_p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>


<div class="m_jp-RenderedText m_jp-OutputArea-output">
<pre>C:\Users\abeer\AppData\Local\<wbr>Temp\ipykernel_17132\<wbr>2538813300.py:1: SettingWithCopyWarning: 
A value is trying to be set on a copy of a slice from a DataFrame.
Try using .loc[row_indexer,col_indexer] = value instead

See the caveats in the documentation: <a href="https://www.google.com/url?q=https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html%23returning-a-view-versus-a-copy&amp;source=gmail-html&amp;ust=1690055563884000&amp;usg=AOvVaw2W3vwM2RSZN0p2ZLwrWk2n" target="_blank" rel="noreferrer">https://pandas.pydata.org/<wbr>pandas-docs/stable/user_guide/<wbr>indexing.html#returning-a-<wbr>view-versus-a-copy</a>
  df[&#39;timestamp&#39;] = pd.to_datetime(df[&#39;timestamp&#39;]<wbr>,errors=&#39;coerce&#39; )
</pre>
</div>
</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [12]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">df</span><span class="m_p">[</span><span class="m_s1">&#39;unix_timestamp&#39;</span><span class="m_p">]</span> <span class="m_o">=</span> <span class="m_n">df</span><span class="m_p">[</span><span class="m_s1">&#39;timestamp&#39;</span><span class="m_p">]</span><span class="m_o">.</span><span class="m_n">astype</span><span class="m_p">(</span><span class="m_s1">&#39;<wbr>datetime64[s]&#39;</span><span class="m_p">)</span><span class="m_o">.</span><span class="m_n">astype</span><span class="m_p">(</span><span class="m_s1">&#39;int64&#39;</span><span class="m_p"><wbr>)</span>

<span class="m_c1"># print the updated DataFrame</span>
<span class="m_nb">print</span><span class="m_p">(</span><span class="m_n">df</span><span class="m_p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>


<div class="m_jp-RenderedText m_jp-OutputArea-output">
<pre>             Date      Time  Latitude  Longitude   Depth  Magnitude  \
0      01/02/1965  13:44:18   19.2460   145.6160  131.60        6.0   
1      01/04/1965  11:29:49    1.8630   127.3520   80.00        5.8   
2      01/05/1965  18:05:58  -20.5790  -173.9720   20.00        6.2   
3      01/08/1965  18:49:43  -59.0760   -23.5570   15.00        5.8   
4      01/09/1965  13:32:50   11.9380   126.4270   15.00        5.8   
...           ...       ...       ...        ...     ...        ...   
23407  12/28/2016  08:22:12   38.3917  -118.8941   12.30        5.6   
23408  12/28/2016  09:13:47   38.3777  -118.8957    8.80        5.5   
23409  12/28/2016  12:38:51   36.9179   140.4262   10.00        5.9   
23410  12/29/2016  22:30:19   -9.0283   118.6639   79.00        6.3   
23411  12/30/2016  20:08:28   37.3973   141.4103   11.94        5.5   

                timestamp       unix_timestamp  
0     1965-01-02 13:44:18  -157630542000000000  
1     1965-01-04 11:29:49  -157465811000000000  
2     1965-01-05 18:05:58  -157355642000000000  
3     1965-01-08 18:49:43  -157093817000000000  
4     1965-01-09 13:32:50  -157026430000000000  
...                   ...                  ...  
23407 2016-12-28 08:22:12  1482913332000000000  
23408 2016-12-28 09:13:47  1482916427000000000  
23409 2016-12-28 12:38:51  1482928731000000000  
23410 2016-12-29 22:30:19  1483050619000000000  
23411 2016-12-30 20:08:28  1483128508000000000  

[23412 rows x 8 columns]
</pre>
</div>
</div>
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>


<div class="m_jp-RenderedText m_jp-OutputArea-output">
<pre>C:\Users\abeer\AppData\Local\<wbr>Temp\ipykernel_17132\<wbr>2211712746.py:1: SettingWithCopyWarning: 
A value is trying to be set on a copy of a slice from a DataFrame.
Try using .loc[row_indexer,col_indexer] = value instead

See the caveats in the documentation: <a href="https://www.google.com/url?q=https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html%23returning-a-view-versus-a-copy&amp;source=gmail-html&amp;ust=1690055563884000&amp;usg=AOvVaw2W3vwM2RSZN0p2ZLwrWk2n" target="_blank" rel="noreferrer">https://pandas.pydata.org/<wbr>pandas-docs/stable/user_guide/<wbr>indexing.html#returning-a-<wbr>view-versus-a-copy</a>
  df[&#39;unix_timestamp&#39;] = df[&#39;timestamp&#39;].astype(&#39;<wbr>datetime64[s]&#39;).astype(&#39;int64&#39;<wbr>)
</pre>
</div>
</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell m_jp-mod-noOutputs">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [13]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_c1"># df[&#39;timestamp&#39;] = pd.to_datetime(df.timestamp, format=&#39;%m/%d/%Y %H:%M:%S&#39;)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [14]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">df</span><span class="m_p">[</span><span class="m_s1">&#39;float_timestamp&#39;</span><span class="m_p">]</span> <span class="m_o">=</span> <span class="m_p">(</span><span class="m_n">df</span><span class="m_p">[</span><span class="m_s1">&#39;timestamp&#39;</span><span class="m_p">]</span><span class="m_o">.</span><span class="m_n">astype</span><span class="m_p">(</span><span class="m_s1">&#39;<wbr>datetime64[s]&#39;</span><span class="m_p">)</span><span class="m_o">.</span><span class="m_n">astype</span><span class="m_p">(</span><span class="m_s1">&#39;int64&#39;</span><span class="m_p"><wbr>)</span> <span class="m_o">/</span> <span class="m_mf">1e9</span><span class="m_p">)</span><span class="m_o">.</span><span class="m_n">astype</span><span class="m_p">(</span><span class="m_s1">&#39;float64&#39;</span><span class="m_p">)</span>

<span class="m_c1"># print the updated DataFrame</span>
<span class="m_nb">print</span><span class="m_p">(</span><span class="m_n">df</span><span class="m_p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>


<div class="m_jp-RenderedText m_jp-OutputArea-output">
<pre>             Date      Time  Latitude  Longitude   Depth  Magnitude  \
0      01/02/1965  13:44:18   19.2460   145.6160  131.60        6.0   
1      01/04/1965  11:29:49    1.8630   127.3520   80.00        5.8   
2      01/05/1965  18:05:58  -20.5790  -173.9720   20.00        6.2   
3      01/08/1965  18:49:43  -59.0760   -23.5570   15.00        5.8   
4      01/09/1965  13:32:50   11.9380   126.4270   15.00        5.8   
...           ...       ...       ...        ...     ...        ...   
23407  12/28/2016  08:22:12   38.3917  -118.8941   12.30        5.6   
23408  12/28/2016  09:13:47   38.3777  -118.8957    8.80        5.5   
23409  12/28/2016  12:38:51   36.9179   140.4262   10.00        5.9   
23410  12/29/2016  22:30:19   -9.0283   118.6639   79.00        6.3   
23411  12/30/2016  20:08:28   37.3973   141.4103   11.94        5.5   

                timestamp       unix_timestamp  float_timestamp  
0     1965-01-02 13:44:18  -157630542000000000    -1.576305e+08  
1     1965-01-04 11:29:49  -157465811000000000    -1.574658e+08  
2     1965-01-05 18:05:58  -157355642000000000    -1.573556e+08  
3     1965-01-08 18:49:43  -157093817000000000    -1.570938e+08  
4     1965-01-09 13:32:50  -157026430000000000    -1.570264e+08  
...                   ...                  ...              ...  
23407 2016-12-28 08:22:12  1482913332000000000     1.482913e+09  
23408 2016-12-28 09:13:47  1482916427000000000     1.482916e+09  
23409 2016-12-28 12:38:51  1482928731000000000     1.482929e+09  
23410 2016-12-29 22:30:19  1483050619000000000     1.483051e+09  
23411 2016-12-30 20:08:28  1483128508000000000     1.483129e+09  

[23412 rows x 9 columns]
</pre>
</div>
</div>
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>


<div class="m_jp-RenderedText m_jp-OutputArea-output">
<pre>C:\Users\abeer\AppData\Local\<wbr>Temp\ipykernel_17132\<wbr>2322599523.py:1: SettingWithCopyWarning: 
A value is trying to be set on a copy of a slice from a DataFrame.
Try using .loc[row_indexer,col_indexer] = value instead

See the caveats in the documentation: <a href="https://www.google.com/url?q=https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html%23returning-a-view-versus-a-copy&amp;source=gmail-html&amp;ust=1690055563884000&amp;usg=AOvVaw2W3vwM2RSZN0p2ZLwrWk2n" target="_blank" rel="noreferrer">https://pandas.pydata.org/<wbr>pandas-docs/stable/user_guide/<wbr>indexing.html#returning-a-<wbr>view-versus-a-copy</a>
  df[&#39;float_timestamp&#39;] = (df[&#39;timestamp&#39;].astype(&#39;<wbr>datetime64[s]&#39;).astype(&#39;int64&#39;<wbr>) / 1e9).astype(&#39;float64&#39;)
</pre>
</div>
</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell m_jp-mod-noOutputs">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [71]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">X</span> <span class="m_o">=</span> <span class="m_n">df</span><span class="m_p">[[</span><span class="m_s1">&#39;float_timestamp&#39;</span><span class="m_p">,</span><span class="m_s1">&#39;<wbr>Latitude&#39;</span><span class="m_p">,</span> <span class="m_s1">&#39;Longitude&#39;</span><span class="m_p">]]</span>
<span class="m_n">y</span> <span class="m_o">=</span> <span class="m_n">df</span><span class="m_p">[[</span><span class="m_s1">&#39;Magnitude&#39;</span><span class="m_p">,</span> <span class="m_s1">&#39;Depth&#39;</span><span class="m_p">]]</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [72]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_kn">from</span> <span class="m_nn">sklearn.model_selection</span> <span class="m_kn">import</span> <span class="m_n">train_test_split</span>

<span class="m_n">X_train</span><span class="m_p">,</span> <span class="m_n">X_test</span><span class="m_p">,</span> <span class="m_n">y_train</span><span class="m_p">,</span> <span class="m_n">y_test</span> <span class="m_o">=</span> <span class="m_n">train_test_split</span><span class="m_p">(</span><span class="m_n">X</span><span class="m_p">,</span> <span class="m_n">y</span><span class="m_p">,</span> <span class="m_n">test_size</span><span class="m_o">=</span><span class="m_mf">0.15</span><span class="m_p">,</span> <span class="m_n">random_state</span><span class="m_o">=</span><span class="m_mi">42</span><span class="m_p">)</span>
<span class="m_nb">print</span><span class="m_p">(</span><span class="m_n">X_train</span><span class="m_o">.</span><span class="m_n">shape</span><span class="m_p">,</span> <span class="m_n">X_test</span><span class="m_o">.</span><span class="m_n">shape</span><span class="m_p">,</span> <span class="m_n">y_train</span><span class="m_o">.</span><span class="m_n">shape</span><span class="m_p">,</span> <span class="m_n">y_test</span><span class="m_o">.</span><span class="m_n">shape</span><span class="m_p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>


<div class="m_jp-RenderedText m_jp-OutputArea-output">
<pre>(19900, 3) (3512, 3) (19900, 2) (3512, 2)
</pre>
</div>
</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [73]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_kn">from</span> <span class="m_nn">sklearn.ensemble</span> <span class="m_kn">import</span> <span class="m_n">RandomForestRegressor</span>

<span class="m_n">reg</span> <span class="m_o">=</span> <span class="m_n">RandomForestRegressor</span><span class="m_p">(</span><span class="m_n">random_<wbr>state</span><span class="m_o">=</span><span class="m_mi">42</span><span class="m_p">)</span>
<span class="m_n">reg</span><span class="m_o">.</span><span class="m_n">fit</span><span class="m_p">(</span><span class="m_n">X_train</span><span class="m_p">,</span> <span class="m_n">y_train</span><span class="m_p">)</span>
<span class="m_n">reg</span><span class="m_o">.</span><span class="m_n">predict</span><span class="m_p">(</span><span class="m_n">X_test</span><span class="m_p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child m_jp-OutputArea-executeResult">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt">Out[73]:</div>




<div class="m_jp-RenderedText m_jp-OutputArea-output m_jp-OutputArea-executeResult">
<pre>array([[  5.884 ,  52.737 ],
       [  5.662 ,  10.464 ],
       [  5.703 ,  63.143 ],
       ...,
       [  5.666 ,  10.    ],
       [  5.845 ,  13.837 ],
       [  6.846 , 616.0472]])</pre>
</div>

</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [74]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">reg</span><span class="m_o">.</span><span class="m_n">score</span><span class="m_p">(</span><span class="m_n">X_test</span><span class="m_p">,</span> <span class="m_n">y_test</span><span class="m_p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child m_jp-OutputArea-executeResult">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt">Out[74]:</div>




<div class="m_jp-RenderedText m_jp-OutputArea-output m_jp-OutputArea-executeResult">
<pre>0.38691128166625305</pre>
</div>

</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [75]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">df</span><span class="m_o">.</span><span class="m_n">corr</span><span class="m_p">()</span> 
<span class="m_n">a</span><span class="m_o">=</span> <span class="m_n">df</span><span class="m_o">.</span><span class="m_n">corr</span><span class="m_p">()</span> 
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>


<div class="m_jp-RenderedText m_jp-OutputArea-output">
<pre>C:\Users\abeer\AppData\Local\<wbr>Temp\ipykernel_17132\<wbr>1330498997.py:1: FutureWarning: The default value of numeric_only in DataFrame.corr is deprecated. In a future version, it will default to False. Select only valid columns or specify the value of numeric_only to silence this warning.
  df.corr()
C:\Users\abeer\AppData\Local\<wbr>Temp\ipykernel_17132\<wbr>1330498997.py:2: FutureWarning: The default value of numeric_only in DataFrame.corr is deprecated. In a future version, it will default to False. Select only valid columns or specify the value of numeric_only to silence this warning.
  a= df.corr()
</pre>
</div>
</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [76]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_kn">import</span> <span class="m_nn">seaborn</span> <span class="m_k">as</span> <span class="m_nn">sns</span>
<span class="m_n">sns</span><span class="m_o">.</span><span class="m_n">heatmap</span><span class="m_p">(</span><span class="m_n">a</span><span class="m_p">,</span> <span class="m_n">annot</span><span class="m_o">=</span><span class="m_kc">True</span><span class="m_p">,</span> <span class="m_n">cmap</span><span class="m_o">=</span><span class="m_s1">&#39;coolwarm&#39;</span><span class="m_p">)</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">show</span><span class="m_p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>




<div class="m_jp-RenderedImage m_jp-OutputArea-output">
<img>
</div>

</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [21]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_kn">from</span> <span class="m_nn">sklearn.model_selection</span> <span class="m_kn">import</span> <span class="m_n">GridSearchCV</span>

<span class="m_n">parameters</span> <span class="m_o">=</span> <span class="m_p">{</span><span class="m_s1">&#39;n_estimators&#39;</span><span class="m_p">:[</span><span class="m_mi">10</span><span class="m_p">,</span> <span class="m_mi">20</span><span class="m_p">,</span> <span class="m_mi">50</span><span class="m_p">,</span> <span class="m_mi">100</span><span class="m_p">,</span> <span class="m_mi">200</span><span class="m_p">,</span> <span class="m_mi">500</span><span class="m_p">]}</span>

<span class="m_n">grid_obj</span> <span class="m_o">=</span> <span class="m_n">GridSearchCV</span><span class="m_p">(</span><span class="m_n">reg</span><span class="m_p">,</span> <span class="m_n">parameters</span><span class="m_p">)</span>
<span class="m_n">grid_fit</span> <span class="m_o">=</span> <span class="m_n">grid_obj</span><span class="m_o">.</span><span class="m_n">fit</span><span class="m_p">(</span><span class="m_n">X_train</span><span class="m_p">,</span> <span class="m_n">y_train</span><span class="m_p">)</span>
<span class="m_n">best_fit</span> <span class="m_o">=</span> <span class="m_n">grid_fit</span><span class="m_o">.</span><span class="m_n">best_estimator_</span>
<span class="m_n">best_fit</span><span class="m_o">.</span><span class="m_n">predict</span><span class="m_p">(</span><span class="m_n">X_test</span><span class="m_p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child m_jp-OutputArea-executeResult">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt">Out[21]:</div>




<div class="m_jp-RenderedText m_jp-OutputArea-output m_jp-OutputArea-executeResult">
<pre>array([[  5.8908  ,  56.0784  ],
       [  5.6854  ,  10.450016],
       [  5.7174  ,  63.3194  ],
       ...,
       [  5.6742  ,   9.98    ],
       [  5.7994  ,  12.796   ],
       [  6.8582  , 615.1823  ]])</pre>
</div>

</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [19]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">best_fit</span><span class="m_o">.</span><span class="m_n">score</span><span class="m_p">(</span><span class="m_n">X_test</span><span class="m_p">,</span> <span class="m_n">y_test</span><span class="m_p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child m_jp-OutputArea-executeResult">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt">Out[19]:</div>




<div class="m_jp-RenderedText m_jp-OutputArea-output m_jp-OutputArea-executeResult">
<pre>0.3905790562324445</pre>
</div>

</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell m_jp-mod-noOutputs">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [20]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_kn">from</span> <span class="m_nn">keras.models</span> <span class="m_kn">import</span> <span class="m_n">Sequential</span>
<span class="m_kn">from</span> <span class="m_nn">keras.layers</span> <span class="m_kn">import</span> <span class="m_n">Dense</span>

<span class="m_k">def</span> <span class="m_nf">create_model</span><span class="m_p">(</span><span class="m_n">neurons</span><span class="m_p">,</span> <span class="m_n">activation</span><span class="m_p">,</span> <span class="m_n">optimizer</span><span class="m_p">,</span> <span class="m_n">loss</span><span class="m_p">):</span>
    <span class="m_n">model</span> <span class="m_o">=</span> <span class="m_n">Sequential</span><span class="m_p">()</span>
    <span class="m_n">model</span><span class="m_o">.</span><span class="m_n">add</span><span class="m_p">(</span><span class="m_n">Dense</span><span class="m_p">(</span><span class="m_n">neurons</span><span class="m_p">,</span> <span class="m_n">activation</span><span class="m_o">=</span><span class="m_n">activation</span><span class="m_p">,</span> <span class="m_n">input_shape</span><span class="m_o">=</span><span class="m_p">(</span><span class="m_mi">3</span><span class="m_p">,)))</span>
    <span class="m_n">model</span><span class="m_o">.</span><span class="m_n">add</span><span class="m_p">(</span><span class="m_n">Dense</span><span class="m_p">(</span><span class="m_n">neurons</span><span class="m_p">,</span> <span class="m_n">activation</span><span class="m_o">=</span><span class="m_n">activation</span><span class="m_p">))</span>
    <span class="m_n">model</span><span class="m_o">.</span><span class="m_n">add</span><span class="m_p">(</span><span class="m_n">Dense</span><span class="m_p">(</span><span class="m_mi">2</span><span class="m_p">,</span> <span class="m_n">activation</span><span class="m_o">=</span><span class="m_s1">&#39;softmax&#39;</span><span class="m_p">))</span>
    
    <span class="m_n">model</span><span class="m_o">.</span><span class="m_n">compile</span><span class="m_p">(</span><span class="m_n">optimizer</span><span class="m_o">=</span><span class="m_n">optimi<wbr>zer</span><span class="m_p">,</span> <span class="m_n">loss</span><span class="m_o">=</span><span class="m_n">loss</span><span class="m_p">,</span> <span class="m_n">metrics</span><span class="m_o">=</span><span class="m_p">[</span><span class="m_s1">&#39;accuracy&#39;</span><span class="m_p">])</span>
    
    <span class="m_k">return</span> <span class="m_n">model</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [21]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_kn">from</span> <span class="m_nn">keras.wrappers.scikit_learn</span> <span class="m_kn">import</span> <span class="m_n">KerasClassifier</span>

<span class="m_n">model</span> <span class="m_o">=</span> <span class="m_n">KerasClassifier</span><span class="m_p">(</span><span class="m_n">build_fn</span><span class="m_o">=</span><span class="m_n">creat<wbr>e_model</span><span class="m_p">,</span> <span class="m_n">verbose</span><span class="m_o">=</span><span class="m_mi">0</span><span class="m_p">)</span>

<span class="m_c1"># neurons = [16, 64, 128, 256]</span>
<span class="m_n">neurons</span> <span class="m_o">=</span> <span class="m_p">[</span><span class="m_mi">16</span><span class="m_p">]</span>
<span class="m_c1"># batch_size = [10, 20, 50, 100]</span>
<span class="m_n">batch_size</span> <span class="m_o">=</span> <span class="m_p">[</span><span class="m_mi">10</span><span class="m_p">]</span>
<span class="m_n">epochs</span> <span class="m_o">=</span> <span class="m_p">[</span><span class="m_mi">10</span><span class="m_p">]</span>
<span class="m_c1"># activation = [&#39;relu&#39;, &#39;tanh&#39;, &#39;sigmoid&#39;, &#39;hard_sigmoid&#39;, &#39;linear&#39;, &#39;exponential&#39;]</span>
<span class="m_n">activation</span> <span class="m_o">=</span> <span class="m_p">[</span><span class="m_s1">&#39;sigmoid&#39;</span><span class="m_p">,</span> <span class="m_s1">&#39;relu&#39;</span><span class="m_p">]</span>
<span class="m_c1"># optimizer = [&#39;SGD&#39;, &#39;RMSprop&#39;, &#39;Adagrad&#39;, &#39;Adadelta&#39;, &#39;Adam&#39;, &#39;Adamax&#39;, &#39;Nadam&#39;]</span>
<span class="m_n">optimizer</span> <span class="m_o">=</span> <span class="m_p">[</span><span class="m_s1">&#39;SGD&#39;</span><span class="m_p">,</span> <span class="m_s1">&#39;Adadelta&#39;</span><span class="m_p">]</span>
<span class="m_n">loss</span> <span class="m_o">=</span> <span class="m_p">[</span><span class="m_s1">&#39;squared_hinge&#39;</span><span class="m_p">]</span>

<span class="m_n">param_grid</span> <span class="m_o">=</span> <span class="m_nb">dict</span><span class="m_p">(</span><span class="m_n">neurons</span><span class="m_o">=</span><span class="m_n">neurons</span><span class="m_p">,</span> <span class="m_n">batch_size</span><span class="m_o">=</span><span class="m_n">batch_size</span><span class="m_p">,</span> <span class="m_n">epochs</span><span class="m_o">=</span><span class="m_n">epochs</span><span class="m_p">,</span> <span class="m_n">activation</span><span class="m_o">=</span><span class="m_n">activation</span><span class="m_p">,</span> <span class="m_n">optimizer</span><span class="m_o">=</span><span class="m_n">optimizer</span><span class="m_p">,</span> <span class="m_n">loss</span><span class="m_o">=</span><span class="m_n">loss</span><span class="m_p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>


<div class="m_jp-RenderedText m_jp-OutputArea-output">
<pre>C:\Users\abeer\AppData\Local\<wbr>Temp\ipykernel_12540\<wbr>3896027448.py:3: DeprecationWarning: KerasClassifier is deprecated, use Sci-Keras (<a href="https://www.google.com/url?q=https://github.com/adriangb/scikeras&amp;source=gmail-html&amp;ust=1690055563885000&amp;usg=AOvVaw1guF8htGxjc4x9jvVXR_kl" target="_blank" rel="noreferrer">https://github.com/adriangb/<wbr>scikeras</a>) instead. See <a href="https://www.google.com/url?q=https://www.adriangb.com/scikeras/stable/migration.html&amp;source=gmail-html&amp;ust=1690055563885000&amp;usg=AOvVaw1jTdg4eTZ-7wwh_Y9rx-mW" target="_blank" rel="noreferrer">https://www.adriangb.com/<wbr>scikeras/stable/migration.html</a> for help migrating.
  model = KerasClassifier(build_fn=<wbr>create_model, verbose=0)
</pre>
</div>
</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [23]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">grid</span> <span class="m_o">=</span> <span class="m_n">GridSearchCV</span><span class="m_p">(</span><span class="m_n">estimator</span><span class="m_o">=</span><span class="m_n">model</span><span class="m_p">,</span> <span class="m_n">param_grid</span><span class="m_o">=</span><span class="m_n">param_grid</span><span class="m_p">,</span> <span class="m_n">n_jobs</span><span class="m_o">=-</span><span class="m_mi">1</span><span class="m_p">)</span>
<span class="m_n">grid_result</span> <span class="m_o">=</span> <span class="m_n">grid</span><span class="m_o">.</span><span class="m_n">fit</span><span class="m_p">(</span><span class="m_n">X_train</span><span class="m_p">,</span> <span class="m_n">y_train</span><span class="m_p">)</span>

<span class="m_nb">print</span><span class="m_p">(</span><span class="m_s2">&quot;Best: </span><span class="m_si">%f</span><span class="m_s2"> using </span><span class="m_si">%s</span><span class="m_s2">&quot;</span> <span class="m_o">%</span> <span class="m_p">(</span><span class="m_n">grid_result</span><span class="m_o">.</span><span class="m_n">best_score_</span><span class="m_p">,</span> <span class="m_n">grid_result</span><span class="m_o">.</span><span class="m_n">best_params_</span><span class="m_p">))</span>
<span class="m_n">means</span> <span class="m_o">=</span> <span class="m_n">grid_result</span><span class="m_o">.</span><span class="m_n">cv_results_</span><span class="m_p">[</span><span class="m_s1">&#39;mean_<wbr>test_score&#39;</span><span class="m_p">]</span>
<span class="m_n">stds</span> <span class="m_o">=</span> <span class="m_n">grid_result</span><span class="m_o">.</span><span class="m_n">cv_results_</span><span class="m_p">[</span><span class="m_s1">&#39;std_<wbr>test_score&#39;</span><span class="m_p">]</span>
<span class="m_n">params</span> <span class="m_o">=</span> <span class="m_n">grid_result</span><span class="m_o">.</span><span class="m_n">cv_results_</span><span class="m_p">[</span><span class="m_s1">&#39;<wbr>params&#39;</span><span class="m_p">]</span>
<span class="m_k">for</span> <span class="m_n">mean</span><span class="m_p">,</span> <span class="m_n">stdev</span><span class="m_p">,</span> <span class="m_n">param</span> <span class="m_ow">in</span> <span class="m_nb">zip</span><span class="m_p">(</span><span class="m_n">means</span><span class="m_p">,</span> <span class="m_n">stds</span><span class="m_p">,</span> <span class="m_n">params</span><span class="m_p">):</span>
    <span class="m_nb">print</span><span class="m_p">(</span><span class="m_s2">&quot;</span><span class="m_si">%f</span><span class="m_s2"> (</span><span class="m_si">%f</span><span class="m_s2">) with: </span><span class="m_si">%r</span><span class="m_s2">&quot;</span> <span class="m_o">%</span> <span class="m_p">(</span><span class="m_n">mean</span><span class="m_p">,</span> <span class="m_n">stdev</span><span class="m_p">,</span> <span class="m_n">param</span><span class="m_p">))</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>


<div class="m_jp-RenderedText m_jp-OutputArea-output">
<pre>Best: 0.600000 using {&#39;activation&#39;: &#39;sigmoid&#39;, &#39;batch_size&#39;: 10, &#39;epochs&#39;: 10, &#39;loss&#39;: &#39;squared_hinge&#39;, &#39;neurons&#39;: 16, &#39;optimizer&#39;: &#39;Adadelta&#39;}
0.413015 (0.479860) with: {&#39;activation&#39;: &#39;sigmoid&#39;, &#39;batch_size&#39;: 10, &#39;epochs&#39;: 10, &#39;loss&#39;: &#39;squared_hinge&#39;, &#39;neurons&#39;: 16, &#39;optimizer&#39;: &#39;SGD&#39;}
0.600000 (0.489898) with: {&#39;activation&#39;: &#39;sigmoid&#39;, &#39;batch_size&#39;: 10, &#39;epochs&#39;: 10, &#39;loss&#39;: &#39;squared_hinge&#39;, &#39;neurons&#39;: 16, &#39;optimizer&#39;: &#39;Adadelta&#39;}
0.411809 (0.427947) with: {&#39;activation&#39;: &#39;relu&#39;, &#39;batch_size&#39;: 10, &#39;epochs&#39;: 10, &#39;loss&#39;: &#39;squared_hinge&#39;, &#39;neurons&#39;: 16, &#39;optimizer&#39;: &#39;SGD&#39;}
0.426131 (0.469169) with: {&#39;activation&#39;: &#39;relu&#39;, &#39;batch_size&#39;: 10, &#39;epochs&#39;: 10, &#39;loss&#39;: &#39;squared_hinge&#39;, &#39;neurons&#39;: 16, &#39;optimizer&#39;: &#39;Adadelta&#39;}
</pre>
</div>
</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell m_jp-mod-noOutputs">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [24]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">model</span> <span class="m_o">=</span> <span class="m_n">Sequential</span><span class="m_p">()</span>
<span class="m_n">model</span><span class="m_o">.</span><span class="m_n">add</span><span class="m_p">(</span><span class="m_n">Dense</span><span class="m_p">(</span><span class="m_mi">16</span><span class="m_p">,</span> <span class="m_n">activation</span><span class="m_o">=</span><span class="m_s1">&#39;relu&#39;</span><span class="m_p">,</span> <span class="m_n">input_shape</span><span class="m_o">=</span><span class="m_p">(</span><span class="m_mi">3</span><span class="m_p">,)))</span>
<span class="m_n">model</span><span class="m_o">.</span><span class="m_n">add</span><span class="m_p">(</span><span class="m_n">Dense</span><span class="m_p">(</span><span class="m_mi">16</span><span class="m_p">,</span> <span class="m_n">activation</span><span class="m_o">=</span><span class="m_s1">&#39;relu&#39;</span><span class="m_p">))</span>
<span class="m_n">model</span><span class="m_o">.</span><span class="m_n">add</span><span class="m_p">(</span><span class="m_n">Dense</span><span class="m_p">(</span><span class="m_mi">2</span><span class="m_p">,</span> <span class="m_n">activation</span><span class="m_o">=</span><span class="m_s1">&#39;softmax&#39;</span><span class="m_p">))</span>

<span class="m_n">model</span><span class="m_o">.</span><span class="m_n">compile</span><span class="m_p">(</span><span class="m_n">optimizer</span><span class="m_o">=</span><span class="m_s1">&#39;SGD&#39;</span><span class="m_p">,</span> <span class="m_n">loss</span><span class="m_o">=</span><span class="m_s1">&#39;squared_hinge&#39;</span><span class="m_p">,</span> <span class="m_n">metrics</span><span class="m_o">=</span><span class="m_p">[</span><span class="m_s1">&#39;accuracy&#39;</span><span class="m_p">])</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [25]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">model</span><span class="m_o">.</span><span class="m_n">fit</span><span class="m_p">(</span><span class="m_n">X_train</span><span class="m_p">,</span> <span class="m_n">y_train</span><span class="m_p">,</span> <span class="m_n">batch_size</span><span class="m_o">=</span><span class="m_mi">10</span><span class="m_p">,</span> <span class="m_n">epochs</span><span class="m_o">=</span><span class="m_mi">20</span><span class="m_p">,</span> <span class="m_n">verbose</span><span class="m_o">=</span><span class="m_mi">1</span><span class="m_p">,</span> <span class="m_n">validation_data</span><span class="m_o">=</span><span class="m_p">(</span><span class="m_n">X_test</span><span class="m_p">,</span> <span class="m_n">y_test</span><span class="m_p">))</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>


<div class="m_jp-RenderedText m_jp-OutputArea-output">
<pre>Epoch 1/20
1990/1990 [=============================<wbr>=] - 15s 7ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 2/20
1990/1990 [=============================<wbr>=] - 12s 6ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 3/20
1990/1990 [=============================<wbr>=] - 9s 5ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 4/20
1990/1990 [=============================<wbr>=] - 11s 5ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 5/20
1990/1990 [=============================<wbr>=] - 10s 5ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 6/20
1990/1990 [=============================<wbr>=] - 9s 4ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 7/20
1990/1990 [=============================<wbr>=] - 9s 4ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 8/20
1990/1990 [=============================<wbr>=] - 8s 4ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 9/20
1990/1990 [=============================<wbr>=] - 10s 5ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 10/20
1990/1990 [=============================<wbr>=] - 9s 5ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 11/20
1990/1990 [=============================<wbr>=] - 9s 4ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 12/20
1990/1990 [=============================<wbr>=] - 9s 4ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 13/20
1990/1990 [=============================<wbr>=] - 10s 5ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 14/20
1990/1990 [=============================<wbr>=] - 10s 5ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 15/20
1990/1990 [=============================<wbr>=] - 10s 5ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 16/20
1990/1990 [=============================<wbr>=] - 9s 5ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 17/20
1990/1990 [=============================<wbr>=] - 10s 5ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 18/20
1990/1990 [=============================<wbr>=] - 10s 5ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 19/20
1990/1990 [=============================<wbr>=] - 9s 5ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
Epoch 20/20
1990/1990 [=============================<wbr>=] - 9s 5ms/step - loss: 0.5038 - accuracy: 0.9809 - val_loss: 0.5040 - val_accuracy: 0.9826
</pre>
</div>
</div>
<div class="m_jp-OutputArea-child m_jp-OutputArea-executeResult">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt">Out[25]:</div>




<div class="m_jp-RenderedText m_jp-OutputArea-output m_jp-OutputArea-executeResult">
<pre>&lt;keras.callbacks.History at 0x1e8857513d0&gt;</pre>
</div>

</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [26]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_p">[</span><span class="m_n">test_loss</span><span class="m_p">,</span> <span class="m_n">test_acc</span><span class="m_p">]</span> <span class="m_o">=</span> <span class="m_n">model</span><span class="m_o">.</span><span class="m_n">evaluate</span><span class="m_p">(</span><span class="m_n">X_test</span><span class="m_p">,</span> <span class="m_n">y_test</span><span class="m_p">)</span>
<span class="m_nb">print</span><span class="m_p">(</span><span class="m_s2">&quot;Evaluation result on Test Data : Loss = </span><span class="m_si">{}</span><span class="m_s2">, accuracy = </span><span class="m_si">{}</span><span class="m_s2">&quot;</span><span class="m_o">.</span><span class="m_n">format</span><span class="m_p">(</span><span class="m_n">test_loss</span><span class="m_p">,</span> <span class="m_n">test_acc</span><span class="m_p">))</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>


<div class="m_jp-RenderedText m_jp-OutputArea-output">
<pre>110/110 [=============================<wbr>=] - 1s 5ms/step - loss: 0.5040 - accuracy: 0.9826
Evaluation result on Test Data : Loss = 0.5040166974067688, accuracy = 0.9826309680938721
</pre>
</div>
</div>

</div>

</div>

</div>
<div class="m_jp-Cell m_jp-MarkdownCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea"><div class="m_jp-InputPrompt m_jp-InputArea-prompt">
</div><div class="m_jp-RenderedHTMLCommon m_jp-RenderedMarkdown m_jp-MarkdownOutput">
<hr>
<h1>Part 2<a rel="noopener noreferrer" class="m_anchor-link" href="#m__Part-2">¶</a></h1><h2>Data Visualization<a rel="noopener noreferrer" class="m_anchor-link" href="#m__Data-Visualization">¶</a></h2>
</div>
</div>
</div>
</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell m_jp-mod-noOutputs">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [168]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_kn">from</span> <span class="m_nn">mpl_toolkits.basemap</span> <span class="m_kn">import</span> <span class="m_n">Basemap</span>

<span class="m_n">m</span> <span class="m_o">=</span> <span class="m_n">Basemap</span><span class="m_p">(</span><span class="m_n">projection</span><span class="m_o">=</span><span class="m_s1">&#39;mill&#39;</span><span class="m_p">,</span><span class="m_n">llcr<wbr>nrlat</span><span class="m_o">=-</span><span class="m_mi">80</span><span class="m_p">,</span><span class="m_n">urcrnrlat</span><span class="m_o">=</span><span class="m_mi">80</span><span class="m_p">,</span> <span class="m_n">llcrnrlon</span><span class="m_o">=-</span><span class="m_mi">180</span><span class="m_p">,</span><span class="m_n">urcrnrlon</span><span class="m_o">=</span><span class="m_mi">180</span><span class="m_p">,</span><span class="m_n">l<wbr>at_ts</span><span class="m_o">=</span><span class="m_mi">20</span><span class="m_p">,</span><span class="m_n">resolution</span><span class="m_o">=</span><span class="m_s1">&#39;c&#39;</span><span class="m_p">)</span>

<span class="m_n">longitudes</span> <span class="m_o">=</span> <span class="m_n">data</span><span class="m_p">[</span><span class="m_s2">&quot;Longitude&quot;</span><span class="m_p">]</span><span class="m_o">.</span><span class="m_n">tolist</span><span class="m_p">()</span>
<span class="m_n">latitudes</span> <span class="m_o">=</span> <span class="m_n">data</span><span class="m_p">[</span><span class="m_s2">&quot;Latitude&quot;</span><span class="m_p">]</span><span class="m_o">.</span><span class="m_n">tolist</span><span class="m_p">()</span>
<span class="m_c1">#m = Basemap(width=12000000,height=<wbr>9000000,projection=&#39;lcc&#39;,</span>
            <span class="m_c1">#resolution=None,lat_1=80.,<wbr>lat_2=55,lat_0=80,lon_0=-107.)</span>
<span class="m_n">x</span><span class="m_p">,</span><span class="m_n">y</span> <span class="m_o">=</span> <span class="m_n">m</span><span class="m_p">(</span><span class="m_n">longitudes</span><span class="m_p">,</span><span class="m_n">latitudes</span><span class="m_p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [169]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">fig</span> <span class="m_o">=</span> <span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">figure</span><span class="m_p">(</span><span class="m_n">figsize</span><span class="m_o">=</span><span class="m_p">(</span><span class="m_mi">12</span><span class="m_p">,</span><span class="m_mi">10</span><span class="m_p">))</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">title</span><span class="m_p">(</span><span class="m_s2">&quot;Major Earthquakes Around the World, 1965-2016&quot;</span><span class="m_p">)</span>
<span class="m_n">m</span><span class="m_o">.</span><span class="m_n">plot</span><span class="m_p">(</span><span class="m_n">x</span><span class="m_p">,</span> <span class="m_n">y</span><span class="m_p">,</span> <span class="m_s2">&quot;o&quot;</span><span class="m_p">,</span> <span class="m_n">markersize</span> <span class="m_o">=</span> <span class="m_mi">2</span><span class="m_p">,</span> <span class="m_n">color</span> <span class="m_o">=</span> <span class="m_s1">&#39;red&#39;</span><span class="m_p">)</span>
<span class="m_n">m</span><span class="m_o">.</span><span class="m_n">drawcoastlines</span><span class="m_p">()</span>
<span class="m_n">m</span><span class="m_o">.</span><span class="m_n">fillcontinents</span><span class="m_p">(</span><span class="m_n">color</span><span class="m_o">=</span><span class="m_s1">&#39;green&#39;</span><span class="m_p"><wbr>,</span><span class="m_n">lake_color</span><span class="m_o">=</span><span class="m_s1">&#39;blue&#39;</span><span class="m_p">)</span>
<span class="m_n">m</span><span class="m_o">.</span><span class="m_n">drawmapboundary</span><span class="m_p">()</span>
<span class="m_n">m</span><span class="m_o">.</span><span class="m_n">drawcountries</span><span class="m_p">()</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">show</span><span class="m_p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>




<div class="m_jp-RenderedImage m_jp-OutputArea-output">
<img>
</div>

</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell m_jp-mod-noOutputs">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [22]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">machine_predictions</span> <span class="m_o">=</span> <span class="m_n">reg</span><span class="m_o">.</span><span class="m_n">predict</span><span class="m_p">(</span><span class="m_n">X_test</span><span class="m_p">)</span>
<span class="m_n">actual_predictions</span> <span class="m_o">=</span> <span class="m_n">y_test</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [33]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_nb">print</span><span class="m_p">(</span><span class="m_nb">type</span><span class="m_p">(</span><span class="m_n">machine_predictions</span><span class="m_p"><wbr>))</span>
<span class="m_nb">print</span><span class="m_p">(</span><span class="m_nb">type</span><span class="m_p">(</span><span class="m_n">actual_predictions</span><span class="m_p">)<wbr>)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>


<div class="m_jp-RenderedText m_jp-OutputArea-output">
<pre>&lt;class &#39;numpy.ndarray&#39;&gt;
&lt;class &#39;pandas.core.frame.DataFrame&#39;&gt;
</pre>
</div>
</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [35]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_nb">print</span><span class="m_p">(</span><span class="m_n">machine_predictions</span><span class="m_o">.</span><span class="m_n">shap<wbr>e</span><span class="m_p">)</span>
<span class="m_nb">print</span><span class="m_p">(</span><span class="m_n">actual_predictions</span><span class="m_o">.</span><span class="m_n">shape</span><span class="m_p"><wbr>)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>


<div class="m_jp-RenderedText m_jp-OutputArea-output">
<pre>(7024,)
(7024,)
</pre>
</div>
</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [157]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_kn">import</span> <span class="m_nn">numpy</span> <span class="m_k">as</span> <span class="m_nn">np</span>

<span class="m_n">machine_predictions</span> <span class="m_o">=</span> <span class="m_n">machine_predictions</span><span class="m_o">.</span><span class="m_n">ravel</span><span class="m_p">()</span>
<span class="m_n">actual_predictions</span> <span class="m_o">=</span> <span class="m_n">actual_predictions</span><span class="m_o">.</span><span class="m_n">ravel</span><span class="m_p">()</span>

<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">hist</span><span class="m_p">([</span><span class="m_n">actual_predictions</span><span class="m_p">,</span> <span class="m_n">machine_predictions</span><span class="m_p">],</span> <span class="m_n">bins</span><span class="m_o">=</span><span class="m_mi">50</span><span class="m_p">,</span> <span class="m_n">color</span><span class="m_o">=</span><span class="m_p">[</span><span class="m_s1">&#39;green&#39;</span><span class="m_p">,</span> <span class="m_s1">&#39;red&#39;</span><span class="m_p">],</span> <span class="m_n">label</span><span class="m_o">=</span><span class="m_p">[</span><span class="m_s1">&#39;Actual&#39;</span><span class="m_p">,</span> <span class="m_s1">&#39;Machine&#39;</span><span class="m_p">])</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">legend</span><span class="m_p">()</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">title</span><span class="m_p">(</span><span class="m_s1">&#39;Comparing Predicted and Actual Earthquake Depths, 1965-2016&#39;</span><span class="m_p">)</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">xlabel</span><span class="m_p">(</span><span class="m_s1">&#39;Depth (Km)&#39;</span><span class="m_p">)</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">ylabel</span><span class="m_p">(</span><span class="m_s1">&#39;Frequency&#39;</span><span class="m_p">)</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">legend</span><span class="m_p">(</span><span class="m_n">loc</span><span class="m_o">=</span><span class="m_s1">&#39;upper right&#39;</span><span class="m_p">,</span> <span class="m_n">fontsize</span><span class="m_o">=</span><span class="m_s1">&#39;large&#39;</span><span class="m_p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child m_jp-OutputArea-executeResult">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt">Out[157]:</div>




<div class="m_jp-RenderedText m_jp-OutputArea-output m_jp-OutputArea-executeResult">
<pre>&lt;matplotlib.legend.Legend at 0x22df8086670&gt;</pre>
</div>

</div>
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>




<div class="m_jp-RenderedImage m_jp-OutputArea-output">
<img>
</div>

</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [159]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">hist</span><span class="m_p">([</span><span class="m_n">actual_predictions</span><span class="m_p">,</span> <span class="m_n">machine_predictions</span><span class="m_p">],</span> <span class="m_n">bins</span><span class="m_o">=</span><span class="m_mi">50</span><span class="m_p">,</span> <span class="m_n">color</span><span class="m_o">=</span><span class="m_p">[</span><span class="m_s1">&#39;green&#39;</span><span class="m_p">,</span> <span class="m_s1">&#39;red&#39;</span><span class="m_p">],</span> <span class="m_n">label</span><span class="m_o">=</span><span class="m_p">[</span><span class="m_s1">&#39;Actual&#39;</span><span class="m_p">,</span> <span class="m_s1">&#39;Machine&#39;</span><span class="m_p">])</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">legend</span><span class="m_p">()</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">xlim</span><span class="m_p">([</span><span class="m_mi">0</span><span class="m_p">,</span> <span class="m_mi">700</span><span class="m_p">])</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">ylim</span><span class="m_p">([</span><span class="m_mi">0</span><span class="m_p">,</span> <span class="m_mi">1000</span><span class="m_p">])</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">xlabel</span><span class="m_p">(</span><span class="m_s1">&#39;Depth (Km)&#39;</span><span class="m_p">)</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">ylabel</span><span class="m_p">(</span><span class="m_s1">&#39;Frequency&#39;</span><span class="m_p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child m_jp-OutputArea-executeResult">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt">Out[159]:</div>




<div class="m_jp-RenderedText m_jp-OutputArea-output m_jp-OutputArea-executeResult">
<pre>Text(0, 0.5, &#39;Frequency&#39;)</pre>
</div>

</div>
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>




<div class="m_jp-RenderedImage m_jp-OutputArea-output">
<img>
</div>

</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [145]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">magnitudes</span> <span class="m_o">=</span> <span class="m_n">data</span><span class="m_p">[</span><span class="m_s1">&#39;Magnitude&#39;</span><span class="m_p">]</span>

<span class="m_c1"># create a histogram</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">hist</span><span class="m_p">(</span><span class="m_n">magnitudes</span><span class="m_p">,</span> <span class="m_n">bins</span><span class="m_o">=</span><span class="m_mi">15</span><span class="m_p">,</span> <span class="m_n">color</span><span class="m_o">=</span><span class="m_s1">&#39;green&#39;</span><span class="m_p">)</span>

<span class="m_c1"># add x and y labels</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">xlabel</span><span class="m_p">(</span><span class="m_s1">&#39;Magnitude&#39;</span><span class="m_p">)</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">ylabel</span><span class="m_p">(</span><span class="m_s1">&#39;Frequency&#39;</span><span class="m_p">)</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">title</span><span class="m_p">(</span><span class="m_s1">&#39;Histogram of Actual Magnitudes&#39;</span><span class="m_p">)</span>

<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">xlim</span><span class="m_p">([</span><span class="m_mi">5</span><span class="m_p">,</span> <span class="m_mf">9.0</span><span class="m_p">])</span>



<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">show</span><span class="m_p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>




<div class="m_jp-RenderedImage m_jp-OutputArea-output">
<img>
</div>

</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [146]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span><span class="m_n">predictions</span> <span class="m_o">=</span> <span class="m_n">reg</span><span class="m_o">.</span><span class="m_n">predict</span><span class="m_p">(</span><span class="m_n">X_test</span><span class="m_p">)</span>  

<span class="m_n">magnitudes</span> <span class="m_o">=</span> <span class="m_n">predictions</span><span class="m_p">[:,</span> <span class="m_mi">0</span><span class="m_p">]</span>  

<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">hist</span><span class="m_p">(</span><span class="m_n">magnitudes</span><span class="m_p">,</span> <span class="m_n">bins</span><span class="m_o">=</span><span class="m_mi">15</span><span class="m_p">,</span> <span class="m_n">color</span><span class="m_o">=</span><span class="m_s1">&#39;brown&#39;</span><span class="m_p">)</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">xlabel</span><span class="m_p">(</span><span class="m_s1">&#39;Magnitude&#39;</span><span class="m_p">)</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">ylabel</span><span class="m_p">(</span><span class="m_s1">&#39;Frequency&#39;</span><span class="m_p">)</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">title</span><span class="m_p">(</span><span class="m_s1">&#39;Histogram of Predicted Magnitudes&#39;</span><span class="m_p">)</span>
<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">xlim</span><span class="m_p">(</span><span class="m_mi">5</span><span class="m_p">,</span> <span class="m_mf">9.0</span><span class="m_p">)</span>


<span class="m_n">plt</span><span class="m_o">.</span><span class="m_n">show</span><span class="m_p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="m_jp-Cell-outputWrapper">
<div class="m_jp-Collapser m_jp-OutputCollapser m_jp-Cell-outputCollapser">
</div>


<div class="m_jp-OutputArea m_jp-Cell-outputArea">
<div class="m_jp-OutputArea-child">
    
    <div class="m_jp-OutputPrompt m_jp-OutputArea-prompt"></div>




<div class="m_jp-RenderedImage m_jp-OutputArea-output">
<img>
</div>

</div>

</div>

</div>

</div><div class="m_jp-Cell m_jp-CodeCell m_jp-Notebook-cell m_jp-mod-noOutputs">
<div class="m_jp-Cell-inputWrapper">
<div class="m_jp-Collapser m_jp-InputCollapser m_jp-Cell-inputCollapser">
</div>
<div class="m_jp-InputArea m_jp-Cell-inputArea">
<div class="m_jp-InputPrompt m_jp-InputArea-prompt">In [ ]:</div>
<div class="m_jp-CodeMirrorEditor m_jp-Editor m_jp-InputArea-editor">
     <div class="m_CodeMirror m_cm-s-jupyter">
<div class="m_highlight m_hl-ipython3"><pre><span></span> 
</pre></div>

     </div>
</div>
</div>
</div>

</div>









</div></body></html>
