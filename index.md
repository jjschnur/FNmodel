<!-- CSS Stuff -->
<style type="text/css">
 * {text-align:center;}
 h2 {color:black;} 
 h4 {text-align: left;}
 ol, li {text-align: left;}
 table {text-align: left;}
 div {text-align: left; //display: inline-block;
 }
 .button {
  border: none;
  color: white;
  padding: 15px 15px;
  text-decoration: none; //display: inline-block;
  font-size: 16px; //margin: 2px 2px;
  cursor: pointer;
  background-color: #008CBA;
}
p {text-align: left;}
</style>


<!-- HTML Stuff -->
<h2> Risk Prediction for Septic Shock and/or Bacteremia <br> Applied to Pediatric Oncology Patients <br> Presenting with Fever and Neutropenia </h2>

<h4> Instructions: </h4>
<ol>
 <li>Check each risk factor that applies to your patient in the table.</li>
 <li>Click "Calculate Score" button to generate risk output.</li>
</ol> 
  
<table>
  <tr>
    <th>Predictor</th>
    <th>Check if true:</th>
  </tr>
 <tr>
    <td>Hematological Malignancy</td>
    <td><input type="checkbox" id="hemat" name="hemat" value="1.496"> </td>
  </tr>
 <tr>
    <td>Cancer Relapse</td>
    <td><input type="checkbox" id="relapse" name="relapse" value="1.162"> </td>
  </tr>
 <tr>
    <td>Hemoglobin <= 6.95 g/dL</td>
    <td><input type="checkbox" id="hemo" name="hemo" value="1.048"> </td>
  </tr>
 <tr>
    <td>Platelets <= 79,000/μL</td>
    <td><input type="checkbox" id="platelets" name="platelets" value="0.89"> </td>
  </tr>
 <tr>
    <td>Growth Stimulating Factor</td>
    <td><input type="checkbox" id="gsf" name="gsf" value="0.748"> </td>
  </tr>
  <tr>
    <td>Age (Years) > 9.79</td>
    <td><input type="checkbox" id="age" name="age" value="0.596"> </td>
  </tr>
 <tr>
    <td>Absolute Monocyte Count <= 53</td>
    <td><input type="checkbox" id="amc" name="amc" value="0.514"> </td>
  </tr>
 <tr>
    <td>Absolute Neutrophil Count <= 55</td>
    <td><input type="checkbox" id="anc" name="anc" value="0.178"> </td>
  </tr>
 <tr>
    <td>Leukocyte Count <= 650</td>
    <td><input type="checkbox" id="leuk" name="leuk" value="0.417"> </td>
  </tr>
 <tr>
    <td>Days Since Chemotherapy Treatment > 10.5</td>
    <td><input type="checkbox" id="days" name="days" value="0.031"> </td>
  </tr>
 <tr>
    <td>Sex = Female</td>
    <td><input type="checkbox" id="sex" name="sex" value="0.477"> </td>
  </tr>
</table>

<div>  
 <button class="button" id="calcbutton"> Calculate Score </button>
 <p id="riskscore">Risk Score: N/A </p>
</div>

<!-- JavaScript Stuff -->
<script>
 
 function changeScore(){
  var hemat = parseFloat(document.getElementById("hemat").value) * document.getElementById("hemat").checked;
  var relapse = parseFloat(document.getElementById("relapse").value) * document.getElementById("relapse").checked;
  var hemo = parseFloat(document.getElementById("hemo").value) * document.getElementById("hemo").checked;
  var platelets = parseFloat(document.getElementById("platelets").value) * document.getElementById("platelets").checked;
  var gsf = parseFloat(document.getElementById("gsf").value) * document.getElementById("gsf").checked;
  var age = parseFloat(document.getElementById("age").value) * document.getElementById("age").checked;
  var amc = parseFloat(document.getElementById("amc").value) * document.getElementById("amc").checked;
  var anc = parseFloat(document.getElementById("anc").value) * document.getElementById("anc").checked;
  var leuk = parseFloat(document.getElementById("leuk").value) * document.getElementById("leuk").checked;
  var days = parseFloat(document.getElementById("days").value) * document.getElementById("days").checked;
  var sex = parseFloat(document.getElementById("sex").value) * document.getElementById("sex").checked;
  let constant = -3.228;
  
  let risk = (1/(1 + Math.exp(-(hemat+relapse+hemo+platelets+gsf+age+amc+anc+leuk+days+sex+constant)))).toFixed(4);
  var level;
  if(risk >= 0.3820){
      var level = "    (High Risk)";
  }else {
      var level = "    (Low Risk)";
  }
  document.getElementById("riskscore").innerHTML = "Risk Score: " + risk + level;
 }
 
 document.getElementById("calcbutton").addEventListener("click", changeScore);
 
</script>
<!--
You can use the [editor on GitHub](https://github.com/jjschnur/FNmodel/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.


### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/jjschnur/FNmodel/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out. 
-->

