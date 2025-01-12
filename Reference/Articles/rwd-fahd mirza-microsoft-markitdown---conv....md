---
authors: Fahd Mirza
categories:
date: 2024-12-23
draft: true
source-url: https://www.youtube.com/watch?v=v65Oyddfxeg
mediums: articles
notes: reference
tags: readwise, reference/articles, consumed
title: Reference - Microsoft MarkItDown - Convert Files and Office Documents to Markdown - Install Locally
---
## Microsoft MarkItDown - Convert Files and Office Documents to Markdown - Install Locally

![rw-book-cover](https://i.ytimg.com/vi/v65Oyddfxeg/maxresdefault.jpg)

published-date: 2024-12-16

**Link:** [Microsoft MarkItDown - Convert Files and Office Documents to Markdown - Install Locally](https://www.youtube.com/watch?v=v65Oyddfxeg)

## Highlights
### id827471526

> You can use it for indexing, text analysis, dataset generation, and many other use cases.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpgrh2zwr5gp878mex30fpp)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpgrh2zwr5gp878mex30fpp)
[Microsoft's MarkItDown](https://github.com/microsoft/markitdown)
It supports:
- PDF
- PowerPoint
- Word
- Excel
- Images (EXIF metadata and OCR)
- Audio (EXIF metadata and speech transcription)
- HTML
- Text-based formats (CSV, JSON, XML)
- ZIP files (iterates over contents)

### id827472290

> Markdown enables you to format text using simple syntax.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpgy4c32795ear82pvs9ph3)

### id827472300

> markdown files are plain Text files are platform-independent, quite portable.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpgyffac9vgs3etkjagcp66)

### id827472332

> Markdown can be converted to other formats with the help of this tool, including HTML, PDF documents, Excel files, LaTeX files, and the list goes on and on.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpgz5bqnr4c5jf6ptb5tt4d)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpgz5bqnr4c5jf6ptb5tt4d)
This tool: [MarkItDown](https://github.com/microsoft/markitdown)

### id827472676

> So let's create a virtual environment as usual, and now let me install the Markdown which is simple: pip install.
> \- [(View Highlight)](https://read.readwise.io/read/01jfph3tjq8j0bqq9ecvs3048n)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfph3tjq8j0bqq9ecvs3048n)
[MarkItDown](https://github.com/microsoft/markitdown) is written in Python, so best not to mix up your global environment the author suggests using a [virtual environment](https://docs.python.org/3/library/venv.html): `python -m venv /path/to/new/virtual/environment`

### id827473720

> you see we are importing this library, Markdown, and then I am instantiating this Markdown. I'm providing it the path to my own PDF file
> \- [(View Highlight)](https://read.readwise.io/read/01jfph9xfsrbsd7drgvdxffqs7)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfph9xfsrbsd7drgvdxffqs7)
```python
from markitdown import MarkItDown
markitdown = MarkItDown()
result = markitdown.convert("mypdf.pdf")
print(result.text_convert)
```

### id827474182

> Also, you can display it in the Markdown by using Python's IPython library. For that, all you need to do is to just, uh, use this IPython to display, and then display it in the Markdown.
> \- [(View Highlight)](https://read.readwise.io/read/01jfphe7kv6fhr7j7z4d1sa1de)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfphe7kv6fhr7j7z4d1sa1de)
```python
from markitdown import MarkItDown
from IPython.display import Markdown, display
markitdown = MarkItDown()
result = markitdown.convert("mypdf.pdf")
display(Markdown(result.text_content))
```

### id827474287

> now let me show you how you can use it with large language models. Let's do the OCR with it, and then um, I We will be providing it an image; it will do the optical color recognition from that image by using the model—open a model.
>   Then we will display it in the Markdown format.
> \- [(View Highlight)](https://read.readwise.io/read/01jfphhad9p0x52ybsfvre4vd0)

### id827474492

> Simply, we're importing Markdown, and then we are importing the open again. I'm instantiating this open's client and Markdown client. Then Markdown is also getting this LLM and the LLM is GPT-4. We already have set up our API key. This is a local image which I'm getting that I want to convert into the Markdown format. I am just printing the text down without markup, and then the actual markup format here, which I'm displaying.
> \- [(View Highlight)](https://read.readwise.io/read/01jfphk7sp7neqkmh4ga0ktgn3)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfphk7sp7neqkmh4ga0ktgn3)
```python
from markitdown import MarkItDown
from openai import OpenAI
client = OpenAI()
md = MarkItDown(llm_client=client, llm_model="gpt-4o")
result = md.convert("ocr.png")
print(result.text_content)
fromIPython.display import Markdown, display
display(Markdown(result.text_content))
```

### id827474693

> if you don't want to use it in your Jupyter notebook or your Python code. You can also use it as a CLI.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpht45k9pmf9bfm8bkpzbyj)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpht45k9pmf9bfm8bkpzbyj)
```sh
markitdown path/to/mypdf.pdf
```

### id827474767

> you can even use the pipe functionality of Linux, something like that, where we are getting this file and piping it to this MarkItDown with the same result.
> \- [(View Highlight)](https://read.readwise.io/read/01jfphwpn3c7e3vbzhhfdax6yf)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfphwpn3c7e3vbzhhfdax6yf)
```sh
cat /home/Ubuntu/myfiles/mypdf.pdf | markitdown
```

### id827474865

> these tools are so useful when it comes to data handling, data engineering, and data manipulation, because that is a key cornerstone for any LLM applications. Pipelines are generating datasets because if the quality of your dataset is good, your LLM application will be a success.
> \- [(View Highlight)](https://read.readwise.io/read/01jfphz95smabjryvpt5pk4rnk)

### id827474908

> We can use all the tools in Pre-process these data, which are scattered throughout our Excel files, PDF files, Confluence pages, our repos, and all that stuff. That is why it's so useful.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpj0d1vtqcc1zq9cg96999q)

### id827475141

> "Which one is better: this tool, Markdown or DocLink by IPM?" I would say that DocLink is much more diverse
> \- [(View Highlight)](https://read.readwise.io/read/01jfpj2wyq2r2tazzhh30qcjr8)

### id827475166

> I think DocLink is better than this, but I'm more than sure it's a new tool, this Markdown, and it is also going to be good very soon.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpj3d98anvwwq8swaxe7xjp)

### id827475181

> I would highly appreciate it if they could make this work with the local LLMs.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpj3vk29f2d14n0z46npae1)



