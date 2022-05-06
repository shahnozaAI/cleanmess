---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://i.ibb.co/Y8ddRtT/rabbit-in-mist.jpg
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
---

# Clean Your Mess

### How not to go from MVP to Production in ML project

<!--
Covid Joy. Intro.
-->

---
layout: image
image: https://i.ibb.co/sq8K2VL/bunny-graph.jpg
---
<!--
Beautiful MVP.
-->

---

<style>
 .c2 {
  diplay: block;
  margin-left: auto;
  margin-right: 100;
  width: 60%;

}
</style>
<img src="https://i.ibb.co/9GXFDs3/alice-falling.jpg" class="c2">
<!--
Desktop. Cloud. Multiuser. Add feature A B C D. Should be done yesterday, why taking so long? Jira. Rebel.Now we feel like Alica in Wonderland, falling to a rabbit hole and aroud madmans
-->

<!-- ---

<style>
.wrapper {
  display: grid;
  grid-template-columns: 1fr 2fr;
}
p {
  text-align: left;
  padding: 70px 0;
  font-size: small;
}

</style>

<div grid="~ cols-2 gap-2" m="-t-2" class="wrapper">

<div>
<p>“Software Developer
Productivity Loss Due to Technical Debt” - Besker, T., Martini,
A., Bosch, J. 2019. </p>
<p> “The Developer Coefficient:
Software engineering efficiency and its $3
trillion impact on global GDP”  - Stripe, 2018. </p>
</div>

<div>
<img border="rounded" src="https://www.oreilly.com/library/view/the-agile-samurai/9781680500066/images/execution/refactoring/technicalDebt.jpg">

</div>

</div> -->

---

<style>

 .c3 {
  diplay: block;
  margin-left: auto;
  margin-right: auto;
  width: 60%;

}

</style>


- “Software Developer
Productivity Loss Due to Technical Debt” - Besker, T., Martini,
A., Bosch, J. 2019. 
-  “The Developer Coefficient:
Software engineering efficiency and its $3
trillion impact on global GDP”  - Stripe, 2018. 

<img border="rounded" src="https://www.oreilly.com/library/view/the-agile-samurai/9781680500066/images/execution/refactoring/technicalDebt.jpg" class="c3">

---
layout: image
image: https://i.ibb.co/BzCPnHM/drink-me-graph.jpg
---
<!--
Beautiful MVP.
-->

---

# Messy code

```python {all|20-23}

from typing import Optional, Self
from pathlib import Path
import pandas as pd

class CSVLoader:
	
	def __init__(self, path: Path, delimeter: Optional[str] = ",") -> Self:
		
		self.path = path
		self.delimeter = delimeter
		# initial awesome stuff
			
	def load_data(self, **kwargs) -> pd.DataFrame:
		
		self.dataf = pd.read_csv(self.path, sep=self.delimeter, **kwargs)
		# do awesome stuff
		return self.dataf
		
# application: doom code that will change with demand
data_path = Path("path/to/data.csv")
data = CSVLoader(path=data_path, delimeter=";").load_data() 
```

---

# Clean code: Production ready

```python {all|3-7|9|17}
...

class DataLoader(ABC):
	
	@abstractclassmethod
	def load_data(self, **kwargs) -> pd.DataFrame:
		"""Interface to data loading ..."""

class CSVReader(DataReader):
	
	def __init__(self, path: Path, delimeter: Optional[str] = ",") -> Self:
		...

	def load_data(self, **kwargs) -> pd.DataFrame:
		...
		
class PDFReader(DataReader):
	...
```

---

# Clean code: Production ready (continues)

```python {all}

class GetData:
	
	def __init__(self, data_loader: DataLoader) -> Self:
		self.data_loader = data_loader
		
	def load_data(self, **kwargs) -> pd.DataFrame:
		
		return self.data_loader.load_data(**kwargs)

# pseaudo code
data_loader = [CSV|PDF]Reader(...)
dataf = GetData(data_loader=data_loader).load_data()
```

---

<style>
 .c1 {
  diplay: block;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 200;
  width: 50%;
}
h2 {
  text-align: center;

}
</style>
## MVP/PoC code should never see the production light!
<img src="https://external-preview.redd.it/n_6URjVLwfFE2-IMhKV7Kh7Uq9LDqepcz1oNghRkwfY.jpg?auto=webp&s=f6078caf1fbc5bc524a212f2b827299ddbcd86c3" class="c1">

---

<style>
 .c6 {
  diplay: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 500;
  width: 50%;}
 h2{
  text-align: center;
  /* padding: 70px 0; */
}
 h1{
  text-align: center;
}
}
</style>

# Thank you

<div grid="~ cols-2 gap-2" m="-t-2">

<div>

## Prayson W. Daniel

<img border="rounded" src="https://i.ibb.co/94cFzP9/Prayson.png" class="c6">
</div>

<div>

## Shahnoza Bekbulaeva

<img border="rounded" src="https://i.ibb.co/WDH5W7f/Shahnoza.png" class="c6">
</div>

</div>