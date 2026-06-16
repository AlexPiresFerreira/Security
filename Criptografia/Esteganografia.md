
# 🖼️ Esteganografia

> **Tags:** #esteganografia #steganography #ocultacao #covert-channel #security #forensics

---

## 📌 Conceito

**Esteganografia** é a prática de **ocultar** informações dentro de outros dados aparentemente inofensivos, de forma que a **existência** da mensagem secreta não seja detectada.

🎯 **Diferença de Criptografia:**
- **Criptografia:** Torna mensagem **ilegível** (mas visível)
- **Esteganografia:** Torna mensagem **invisível**

**Combinação:** Criptografar + Esteganografar = Dupla proteção

---

## 🎨 Tipos de Esteganografia

### 1️⃣ Esteganografia em Imagens

**Técnica mais comum:** LSB (Least Significant Bit)

#### Como Funciona LSB

**Conceito:** Modificar o **bit menos significativo** de cada pixel sem alterar visivelmente a imagem.

**Exemplo:**

Pixel RGB original: R: 11010110 (214) G: 10110101 (181) B: 11001100 (204)

Mensagem a ocultar: "A" = 01000001

Modificar LSB de cada canal: R: 11010110 → 11010110 (0) - sem mudança G: 10110101 → 10110100 (1) - muda LSB B: 11001100 → 11001100 (0) - sem mudança

Pixel RGB modificado: R: 11010110 (214) - diferença: 0 G: 10110100 (180) - diferença: -1 B: 11001100 (204) - diferença: 0


**Resultado:** Mudança imperceptível ao olho humano!

---

#### Implementação Python (LSB)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-9af5whszv" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">from</span><span> PIL </span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> Image
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> numpy </span><span class="token" style="color:rgb(127, 219, 202)">as</span><span> np
</span>
<span></span><span class="token" style="color:rgb(127, 219, 202)">def</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">text_to_binary</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>text</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token triple-quoted-string" style="color:rgb(173, 219, 103)">&quot;&quot;&quot;Converte texto para binário&quot;&quot;&quot;</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">return</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>join</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(130, 170, 255)">format</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(130, 170, 255)">ord</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>char</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;08b&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">for</span><span> char </span><span class="token" style="color:rgb(127, 219, 202)">in</span><span> text</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(127, 219, 202)">def</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">hide_message</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>image_path</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> message</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> output_path</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token triple-quoted-string" style="color:rgb(173, 219, 103)">&quot;&quot;&quot;Oculta mensagem em imagem usando LSB&quot;&quot;&quot;</span><span>
</span><span>    img </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> Image</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span class="token" style="color:rgb(130, 170, 255)">open</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>image_path</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>    img_array </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> np</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>array</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>img</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span>    </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Converter mensagem para binário</span><span>
</span><span>    binary_message </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> text_to_binary</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>message</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>    binary_message </span><span class="token" style="color:rgb(127, 219, 202)">+=</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;1111111111111110&#x27;</span><span>  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Delimitador (EOF)</span><span>
</span>
<span>    data_index </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">0</span><span>
</span>
<span>    </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Percorrer pixels</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">for</span><span> i </span><span class="token" style="color:rgb(127, 219, 202)">in</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">range</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>img_array</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>shape</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span class="token" style="color:rgb(247, 140, 108)">0</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>        </span><span class="token" style="color:rgb(127, 219, 202)">for</span><span> j </span><span class="token" style="color:rgb(127, 219, 202)">in</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">range</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>img_array</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>shape</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span class="token" style="color:rgb(247, 140, 108)">1</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>            </span><span class="token" style="color:rgb(127, 219, 202)">for</span><span> k </span><span class="token" style="color:rgb(127, 219, 202)">in</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">range</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(247, 140, 108)">3</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># R, G, B</span><span>
</span><span>                </span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> data_index </span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">len</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>binary_message</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>                    </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Modificar LSB</span><span>
</span><span>                    img_array</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>i</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>j</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>k</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">int</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(130, 170, 255)">bin</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>img_array</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>i</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>j</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>k</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span class="token" style="color:rgb(247, 140, 108)">2</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span class="token" style="color:rgb(127, 219, 202)">-</span><span class="token" style="color:rgb(247, 140, 108)">1</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">+</span><span> 
</span><span>                                             binary_message</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>data_index</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">2</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>                    data_index </span><span class="token" style="color:rgb(127, 219, 202)">+=</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1</span><span>
</span>
<span>    </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Salvar imagem modificada</span><span>
</span><span>    result_img </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> Image</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>fromarray</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>img_array</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>    result_img</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>save</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>output_path</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">f&quot;Mensagem oculta em </span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">{</span><span class="token string-interpolation interpolation">output_path</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">}</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(127, 219, 202)">def</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">extract_message</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>image_path</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token triple-quoted-string" style="color:rgb(173, 219, 103)">&quot;&quot;&quot;Extrai mensagem oculta de imagem&quot;&quot;&quot;</span><span>
</span><span>    img </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> Image</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span class="token" style="color:rgb(130, 170, 255)">open</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>image_path</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>    img_array </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> np</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>array</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>img</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span>    binary_message </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;&quot;</span><span>
</span>
<span>    </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair LSBs</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">for</span><span> i </span><span class="token" style="color:rgb(127, 219, 202)">in</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">range</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>img_array</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>shape</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span class="token" style="color:rgb(247, 140, 108)">0</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>        </span><span class="token" style="color:rgb(127, 219, 202)">for</span><span> j </span><span class="token" style="color:rgb(127, 219, 202)">in</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">range</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>img_array</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>shape</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span class="token" style="color:rgb(247, 140, 108)">1</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>            </span><span class="token" style="color:rgb(127, 219, 202)">for</span><span> k </span><span class="token" style="color:rgb(127, 219, 202)">in</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">range</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(247, 140, 108)">3</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># R, G, B</span><span>
</span><span>                binary_message </span><span class="token" style="color:rgb(127, 219, 202)">+=</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">bin</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>img_array</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>i</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>j</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>k</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span class="token" style="color:rgb(127, 219, 202)">-</span><span class="token" style="color:rgb(247, 140, 108)">1</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span>
</span>
<span>    </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Converter binário para texto</span><span>
</span><span>    message </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;&quot;</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">for</span><span> i </span><span class="token" style="color:rgb(127, 219, 202)">in</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">range</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(247, 140, 108)">0</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">len</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>binary_message</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">8</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>        byte </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> binary_message</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>i</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>i</span><span class="token" style="color:rgb(127, 219, 202)">+</span><span class="token" style="color:rgb(247, 140, 108)">8</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span>
</span><span>        </span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> byte </span><span class="token" style="color:rgb(127, 219, 202)">==</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;11111110&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Delimitador</span><span>
</span><span>            </span><span class="token" style="color:rgb(127, 219, 202)">break</span><span>
</span><span>        message </span><span class="token" style="color:rgb(127, 219, 202)">+=</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">chr</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(130, 170, 255)">int</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>byte</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">2</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span>    </span><span class="token" style="color:rgb(127, 219, 202)">return</span><span> message
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Uso</span><span>
</span><span>hide_message</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&quot;original.png&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Mensagem secreta!&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;stego.png&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>extracted </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> extract_message</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&quot;stego.png&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">f&quot;Mensagem extraída: </span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">{</span><span class="token string-interpolation interpolation">extracted</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">}</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span></code></pre></div>

---

#### Ferramentas de Esteganografia em Imagens

##### Steghide
**Descrição:** Ferramenta CLI para ocultar dados em imagens e áudio.

**Instalação:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-rssauptcl" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> steghide
</span></code></pre></div>

**Uso:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-v0tx6awo5" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ocultar arquivo em imagem</span><span>
</span><span>steghide embed </span><span class="token parameter" style="color:rgb(214, 222, 235)">-cf</span><span> imagem.jpg </span><span class="token parameter" style="color:rgb(214, 222, 235)">-ef</span><span> mensagem.txt </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> senha123
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair arquivo de imagem</span><span>
</span><span>steghide extract </span><span class="token parameter" style="color:rgb(214, 222, 235)">-sf</span><span> imagem.jpg </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> senha123
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver informações (sem extrair)</span><span>
</span>steghide info imagem.jpg
</code></pre></div>

---

##### Stegosuite (GUI)
**Instalação:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-yudyczgct" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> stegosuite
</span></code></pre></div>

**Uso:** Interface gráfica amigável para ocultar/extrair dados.

---

##### OpenStego
**Site:** [openstego.com](https://www.openstego.com/)

**Características:**
- GUI Java
- Suporta múltiplos formatos
- Watermarking

---

##### Outguess
**Uso:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ox12c16s8" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ocultar</span><span>
</span><span>outguess </span><span class="token parameter" style="color:rgb(214, 222, 235)">-k</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;senha&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> mensagem.txt original.jpg stego.jpg
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair</span><span>
</span><span>outguess </span><span class="token parameter" style="color:rgb(214, 222, 235)">-k</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;senha&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-r</span><span> stego.jpg mensagem_extraida.txt
</span></code></pre></div>

---

### 2️⃣ Esteganografia em Áudio

#### Técnicas

##### LSB em Áudio
Similar a imagens, modifica bits menos significativos de samples de áudio.

##### Echo Hiding
Adiciona ecos imperceptíveis que codificam dados.

##### Phase Coding
Modifica a fase de componentes de frequência.

---

#### Ferramentas

##### DeepSound
**Plataforma:** Windows

**Características:**
- GUI amigável
- Suporta MP3, WAV, FLAC
- Criptografia AES-256

**Download:** [jpinsoft.net/deepsound](http://jpinsoft.net/deepsound/)

---

##### Sonic Visualiser
**Uso:** Análise de áudio para detectar esteganografia

**Instalação:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-u7ox81h48" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> sonic-visualiser
</span></code></pre></div>

---

### 3️⃣ Esteganografia em Vídeo

**Técnicas:**
- LSB em frames individuais
- Modificação de motion vectors
- Ocultar dados em frames I, P, B

**Ferramentas:**
- **OpenPuff:** Suporta vídeo, imagem, áudio
- **StegoVideo:** Específico para vídeo

---

### 4️⃣ Esteganografia em Texto

#### Técnicas

##### Whitespace Steganography
Usa espaços, tabs e quebras de linha para codificar dados.

**Exemplo:**
```

Texto normal: "Este é um texto normal."

Com espaços extras (invisíveis): "Este é um texto normal." ^^ ^^ (codifica bits)

```
**Ferramenta:** SNOW (Steganographic Nature Of Whitespace)

---

##### Unicode Steganography
Usa caracteres Unicode visualmente idênticos.

**Exemplo:**
```

'a' (U+0061) vs 'а' (U+0430) - Cirílico 'e' (U+0065) vs 'е' (U+0435) - Cirílico

```
---

##### Spam Mimic
**Site:** [spammimic.com](http://www.spammimic.com/)

**Conceito:** Codifica mensagem como spam aparentemente legítimo.

**Exemplo:**
```

Mensagem: "Attack at dawn"

Spam gerado: "Dear Friend, Especially for you - this red-hot investment opportunity! This is a one time mailing…"

```
---

### 5️⃣ Esteganografia em Arquivos

#### Técnicas

##### Concatenação de Arquivos
Adicionar dados ao final de arquivos sem corromper o formato.

**Exemplo:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-pwrftik03" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ocultar arquivo.zip dentro de imagem.jpg</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> imagem.jpg arquivo.zip </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> stego.jpg
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">unzip</span><span> stego.jpg
</span></code></pre></div>

**Funciona com:**
- ZIP (formato permite lixo no início)
- RAR
- Alguns formatos de imagem

---

##### Slack Space
Usar espaço não utilizado em sistemas de arquivos.

**Exemplo:** Cluster de 4KB, arquivo de 1KB = 3KB de slack space disponível.

---

##### Alternate Data Streams (ADS) - Windows NTFS
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">cmd</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-nzjvfjv7m" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-cmd" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span># Criar ADS
</span>echo &quot;Mensagem secreta&quot; &gt; arquivo.txt:hidden.txt
<!-- -->
<!-- --># Ler ADS
<!-- -->more &lt; arquivo.txt:hidden.txt
<!-- -->
<!-- --># Listar ADS
<!-- -->dir /r
</code></pre></div>

---

### 6️⃣ Esteganografia de Rede

#### Covert Channels

##### ICMP Tunneling
Ocultar dados em pacotes ICMP (ping).

**Ferramenta:** ptunnel
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-m8ls6ddbo" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Servidor</span><span>
</span>ptunnel
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Cliente</span><span>
</span><span>ptunnel </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> proxy_server </span><span class="token parameter" style="color:rgb(214, 222, 235)">-lp</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">8000</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-da</span><span> destination_server </span><span class="token parameter" style="color:rgb(214, 222, 235)">-dp</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">80</span><span>
</span></code></pre></div>

---

##### DNS Tunneling
Ocultar dados em queries DNS.

**Ferramentas:**
- **Iodine**
- **dnscat2**

**Exemplo (dnscat2):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-8udbs1d1b" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Servidor</span><span>
</span><span>dnscat2 </span><span class="token parameter" style="color:rgb(214, 222, 235)">--secret</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>senha123 example.com
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Cliente</span><span>
</span><span>dnscat2 </span><span class="token parameter" style="color:rgb(214, 222, 235)">--secret</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>senha123 example.com
</span></code></pre></div>

---

##### HTTP/HTTPS Steganography
Ocultar dados em headers HTTP, cookies, etc.

---

## 🔍 Detecção de Esteganografia (Steganalysis)

### Técnicas de Detecção

#### 1️⃣ Análise Estatística
Detectar anomalias estatísticas em dados.

**Indicadores:**
- Distribuição anormal de LSBs
- Mudanças em histograma
- Padrões incomuns

---

#### 2️⃣ Visual Attack
Análise visual de imagens para detectar distorções.

---

#### 3️⃣ Chi-Square Attack
Teste estatístico para detectar LSB steganography.

---

### Ferramentas de Detecção

#### StegExpose
**Descrição:** Detector de esteganografia LSB.

**Instalação:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-h6cv8p5lx" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">git</span><span> clone https://github.com/b3dk7/StegExpose.git
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">cd</span><span> StegExpose
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">java</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-jar</span><span> StegExpose.jar imagem.png
</span></code></pre></div>

---

#### Stegdetect
**Uso:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-qi5g3rb21" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>stegdetect imagem.jpg
</span></code></pre></div>

**Output:**
```

imagem.jpg : jphide(_*_)

# Indica possível uso de JPHide

```
---

#### Binwalk
**Descrição:** Analisa arquivos em busca de assinaturas embutidas.

**Instalação:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-g95kvo3co" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> binwalk
</span></code></pre></div>

**Uso:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-p12dt92wu" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Analisar arquivo</span><span>
</span>binwalk arquivo.jpg
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair arquivos embutidos</span><span>
</span><span>binwalk </span><span class="token parameter" style="color:rgb(214, 222, 235)">-e</span><span> arquivo.jpg
</span></code></pre></div>

**Exemplo de output:**
```

## DECIMAL HEXADECIMAL DESCRIPTION

0 0x0 JPEG image data 153648 0x25830 Zip archive data

```
---

#### ExifTool
**Descrição:** Examina metadados de arquivos.

**Uso:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ycf3cnmhx" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>exiftool imagem.jpg
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar se há dados suspeitos em metadados</span><span>
</span><span>exiftool </span><span class="token parameter" style="color:rgb(214, 222, 235)">-a</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-G1</span><span> imagem.jpg
</span></code></pre></div>

---

#### Strings
**Descrição:** Extrai strings legíveis de arquivos binários.

**Uso:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-0f5nt7mlq" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>strings imagem.jpg </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;flag\|password\|secret&quot;</span><span>
</span></code></pre></div>

---

## 🎯 Casos de Uso

### Uso Legítimo

#### 1. Watermarking Digital
Proteger direitos autorais embutindo marca d'água invisível.

#### 2. Comunicação Confidencial
Jornalistas e ativistas em regimes repressivos.

#### 3. Forense Digital
Rastrear vazamentos de informação.

---

### Uso Malicioso

#### 1. Exfiltração de Dados
Atacantes ocultam dados roubados em imagens/vídeos aparentemente inofensivos.

#### 2. Malware Distribution
Ocultar malware em imagens para evitar detecção.

#### 3. Command & Control (C2)
Comunicação com malware usando esteganografia.

**Exemplo:** Malware busca comandos em comentários de imagens no Instagram.

---

## 🛠️ Exemplo Prático - CTF Challenge

### Desafio: "Hidden Flag"

**Arquivo fornecido:** `challenge.png`

**Objetivo:** Encontrar a flag oculta.

---

### Passo 1: Análise Básica
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-otqkuvgde" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver informações do arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">file</span><span> challenge.png
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Output: PNG image data, 800 x 600, 8-bit/color RGB</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar metadados</span><span>
</span>exiftool challenge.png
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar strings</span><span>
</span><span>strings challenge.png </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> flag
</span></code></pre></div>

---

### Passo 2: Binwalk
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-shdfb7dkn" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>binwalk challenge.png
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Output:</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># DECIMAL       HEXADECIMAL     DESCRIPTION</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 0             0x0             PNG image</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 153648        0x25830         Zip archive data</span><span>
</span></code></pre></div>

**Achado:** Há um ZIP embutido!

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-2zyq3o0xt" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Extrair</span><span>
</span><span>binwalk </span><span class="token parameter" style="color:rgb(214, 222, 235)">-e</span><span> challenge.png
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar arquivos extraídos</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> _challenge.png.extracted/
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 25830.zip</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Descompactar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">unzip</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">25830</span><span>.zip
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># flag.txt</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ler flag</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> flag.txt
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># flag{st3g0_m4st3r_2024}</span><span>
</span></code></pre></div>

---

### Passo 3: Steghide (se protegido por senha)
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-hdaqqtc10" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Tentar extrair sem senha</span><span>
</span><span>steghide extract </span><span class="token parameter" style="color:rgb(214, 222, 235)">-sf</span><span> challenge.png
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Se pedir senha, tentar comum</span><span>
</span><span>steghide extract </span><span class="token parameter" style="color:rgb(214, 222, 235)">-sf</span><span> challenge.png </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> password
</span><span>steghide extract </span><span class="token parameter" style="color:rgb(214, 222, 235)">-sf</span><span> challenge.png </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">123456</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ou usar stegcracker (brute force)</span><span>
</span>stegcracker challenge.png wordlist.txt
</code></pre></div>

---

### Passo 4: LSB Steganography
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-i1fe2mpkt" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Usar zsteg (Ruby tool)</span><span>
</span><span>gem </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> zsteg
</span>zsteg challenge.png
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Output pode revelar:</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># b1,rgb,lsb,xy       .. text: &quot;flag{hidden_in_lsb}&quot;</span><span>
</span></code></pre></div>

---

## 🔐 Contramedidas

### Para Organizações

#### 1. DLP (Data Loss Prevention)
Detectar tentativas de exfiltração via esteganografia.

#### 2. Análise de Tráfego
Monitorar uploads de imagens/vídeos suspeitos.

#### 3. Políticas
- Bloquear uploads de arquivos pessoais
- Restringir acesso a ferramentas de esteganografia

---

### Para Usuários

#### 1. Verificar Arquivos Recebidos
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-01zqwr47e" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Sempre verificar arquivos com binwalk</span><span>
</span>binwalk arquivo_recebido.jpg
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar metadados</span><span>
</span>exiftool arquivo_recebido.jpg
</code></pre></div>

#### 2. Usar Antivírus Atualizado
Alguns antivírus detectam esteganografia maliciosa.

---

## 📚 Recursos e Ferramentas

### Ferramentas Open Source

| Ferramenta | Tipo | Uso |
|------------|------|-----|
| **Steghide** | CLI | Ocultar/extrair (imagem/áudio) |
| **OpenStego** | GUI | Ocultar/extrair + watermark |
| **Stegosuite** | GUI | Ocultar/extrair (imagens) |
| **Outguess** | CLI | Ocultar/extrair (imagens) |
| **Binwalk** | CLI | Análise/extração de arquivos |
| **StegExpose** | CLI | Detecção de LSB stego |
| **zsteg** | CLI | Detecção em imagens PNG/BMP |
| **Stegcracker** | CLI | Brute force de senhas |

---

### Sites Úteis

- **FutureText:** [futuretext.com](http://www.futuretext.com/) - Esteganografia em texto
- **Spam Mimic:** [spammimic.com](http://www.spammimic.com/) - Codificar mensagens como spam
- **Steganography Online:** [stylesuxx.github.io/steganography](https://stylesuxx.github.io/steganography/) - Ferramenta web

---

## 🎓 Aprendizado e Prática

### CTF Challenges
- **PicoCTF:** Desafios de esteganografia
- **Hack The Box:** Máquinas com stego
- **TryHackMe:** Salas dedicadas a steganography

### Prática
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-no77befhr" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar seu próprio desafio</span><span>
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">1</span><span>. Escolher imagem
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">2</span><span>. Ocultar flag usando steghide
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">3</span><span>. Compartilhar com amigos
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">4</span><span>. Ver quem consegue extrair</span><span class="token" style="color:rgb(127, 219, 202)">!</span><span>
</span></code></pre></div>

---

## 🔗 Links Relacionados

- [[Fundamentos-Cripto]]
- [[Hash]]
- [[OSINT-Fundamentos]]
- [[Forensics]]

---

## 📚 Referências

- Steghide: [steghide.sourceforge.net](http://steghide.sourceforge.net/)
- OpenStego: [openstego.com](https://www.openstego.com/)
- Binwalk: [github.com/ReFirmLabs/binwalk](https://github.com/ReFirmLabs/binwalk)
- Steganalysis: [ws.binghamton.edu/fridrich/](http://ws.binghamton.edu/fridrich/)