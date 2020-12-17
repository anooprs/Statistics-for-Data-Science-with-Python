<center>
    <img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/Logos/organization_logo/organization_logo.png" width="300" alt="cognitiveclass.ai logo"  />
</center>

# Introduction  Notebook

Estaimted time needed: **10** minutes

## Objectives

After completing this lab you will be able to:

-   Acquire data in various ways
-   Obtain insights from Data with Pandas library


<h2>Table of Contents</h2>

<div class="alert alert-block alert-info" style="margin-top: 20px">
<ol>
    <li><a href="#data_acquisition">Data Acquisition</a>
    <li><a href="#basic_insight">Basic Insight of Dataset</a></li>
</ol>

Estimated Time Needed: <strong>10 min</strong>

</div>
<hr>


<h1 id="data_acquisition">Data Acquisition</h1>
<p>
There are various formats for a dataset, .csv, .json, .xlsx  etc. The dataset can be stored in different places, on your local machine or sometimes online.<br>
In this section, you will learn how to load a dataset into our Jupyter Notebook.<br>
In our case, the Automobile Dataset is an online source, and it is in CSV (comma separated value) format. Let's use this dataset as an example to practice data reading.
<ul>
    <li>data source: <a href="https://archive.ics.uci.edu/ml/machine-learning-databases/autos/imports-85.data" target="_blank">https://archive.ics.uci.edu/ml/machine-learning-databases/autos/imports-85.data</a></li>
    <li>data type: csv</li>
</ul>
The Pandas Library is a useful tool that enables us to read various datasets into a data frame; our Jupyter notebook platforms have a built-in <b>Pandas Library</b> so that all we need to do is import Pandas without installing. If you run this notebook in a different environment, e.g. your desktop, you may need to uncomment and install Pandas or Numpy.
</p>



```python
# !pip install pandas
# !pip install numpy
```


```python
# import library
import pandas as pd
import numpy as np
```

<h2>Read Data</h2>
<p>
We use <code>pandas.read_csv()</code> function to read the csv file. In the bracket, we put the file path along with a quotation mark, so that pandas will read the file into a data frame from that address. The file path can be either an URL or your local file address.<br>
Because the data does not include headers, we can add an argument <code>headers = None</code>  inside the  <code>read_csv()</code> method, so that pandas will not automatically set the first row as a header.<br>
You can also assign the dataset to any variable you create.
</p>


This dataset was hosted on IBM Cloud object click <a href="https://cocl.us/DA101EN_object_storage">HERE</a> for free storage.



```python
# Read the online file by the URL provides above, and assign it to variable "df"
other_path = "https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/DA0101EN/auto.csv"
df = pd.read_csv(other_path, header=None)
```

After reading the dataset, we can use the <code>dataframe.head(n)</code> method to check the top n rows of the dataframe; where n is an integer. Contrary to <code>dataframe.head(n)</code>, <code>dataframe.tail(n)</code> will show you the bottom n rows of the dataframe.



```python
# show the first 5 rows using dataframe.head() method
print("The first 5 rows of the dataframe") 
df.head(5)
```

    The first 5 rows of the dataframe





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>8</th>
      <th>9</th>
      <th>...</th>
      <th>16</th>
      <th>17</th>
      <th>18</th>
      <th>19</th>
      <th>20</th>
      <th>21</th>
      <th>22</th>
      <th>23</th>
      <th>24</th>
      <th>25</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3</td>
      <td>?</td>
      <td>alfa-romero</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>convertible</td>
      <td>rwd</td>
      <td>front</td>
      <td>88.6</td>
      <td>...</td>
      <td>130</td>
      <td>mpfi</td>
      <td>3.47</td>
      <td>2.68</td>
      <td>9.0</td>
      <td>111</td>
      <td>5000</td>
      <td>21</td>
      <td>27</td>
      <td>13495</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>?</td>
      <td>alfa-romero</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>convertible</td>
      <td>rwd</td>
      <td>front</td>
      <td>88.6</td>
      <td>...</td>
      <td>130</td>
      <td>mpfi</td>
      <td>3.47</td>
      <td>2.68</td>
      <td>9.0</td>
      <td>111</td>
      <td>5000</td>
      <td>21</td>
      <td>27</td>
      <td>16500</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>?</td>
      <td>alfa-romero</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>hatchback</td>
      <td>rwd</td>
      <td>front</td>
      <td>94.5</td>
      <td>...</td>
      <td>152</td>
      <td>mpfi</td>
      <td>2.68</td>
      <td>3.47</td>
      <td>9.0</td>
      <td>154</td>
      <td>5000</td>
      <td>19</td>
      <td>26</td>
      <td>16500</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>164</td>
      <td>audi</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>fwd</td>
      <td>front</td>
      <td>99.8</td>
      <td>...</td>
      <td>109</td>
      <td>mpfi</td>
      <td>3.19</td>
      <td>3.40</td>
      <td>10.0</td>
      <td>102</td>
      <td>5500</td>
      <td>24</td>
      <td>30</td>
      <td>13950</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>164</td>
      <td>audi</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>4wd</td>
      <td>front</td>
      <td>99.4</td>
      <td>...</td>
      <td>136</td>
      <td>mpfi</td>
      <td>3.19</td>
      <td>3.40</td>
      <td>8.0</td>
      <td>115</td>
      <td>5500</td>
      <td>18</td>
      <td>22</td>
      <td>17450</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 26 columns</p>
</div>



<div class="alert alert-danger alertdanger" style="margin-top: 20px">
<h1> Question #1: </h1>
<b>check the bottom 10 rows of data frame "df".</b>
</div>



```python
# Write your code below and press Shift+Enter to execute 
df.tail(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>8</th>
      <th>9</th>
      <th>...</th>
      <th>16</th>
      <th>17</th>
      <th>18</th>
      <th>19</th>
      <th>20</th>
      <th>21</th>
      <th>22</th>
      <th>23</th>
      <th>24</th>
      <th>25</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>195</th>
      <td>-1</td>
      <td>74</td>
      <td>volvo</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>wagon</td>
      <td>rwd</td>
      <td>front</td>
      <td>104.3</td>
      <td>...</td>
      <td>141</td>
      <td>mpfi</td>
      <td>3.78</td>
      <td>3.15</td>
      <td>9.5</td>
      <td>114</td>
      <td>5400</td>
      <td>23</td>
      <td>28</td>
      <td>13415</td>
    </tr>
    <tr>
      <th>196</th>
      <td>-2</td>
      <td>103</td>
      <td>volvo</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>rwd</td>
      <td>front</td>
      <td>104.3</td>
      <td>...</td>
      <td>141</td>
      <td>mpfi</td>
      <td>3.78</td>
      <td>3.15</td>
      <td>9.5</td>
      <td>114</td>
      <td>5400</td>
      <td>24</td>
      <td>28</td>
      <td>15985</td>
    </tr>
    <tr>
      <th>197</th>
      <td>-1</td>
      <td>74</td>
      <td>volvo</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>wagon</td>
      <td>rwd</td>
      <td>front</td>
      <td>104.3</td>
      <td>...</td>
      <td>141</td>
      <td>mpfi</td>
      <td>3.78</td>
      <td>3.15</td>
      <td>9.5</td>
      <td>114</td>
      <td>5400</td>
      <td>24</td>
      <td>28</td>
      <td>16515</td>
    </tr>
    <tr>
      <th>198</th>
      <td>-2</td>
      <td>103</td>
      <td>volvo</td>
      <td>gas</td>
      <td>turbo</td>
      <td>four</td>
      <td>sedan</td>
      <td>rwd</td>
      <td>front</td>
      <td>104.3</td>
      <td>...</td>
      <td>130</td>
      <td>mpfi</td>
      <td>3.62</td>
      <td>3.15</td>
      <td>7.5</td>
      <td>162</td>
      <td>5100</td>
      <td>17</td>
      <td>22</td>
      <td>18420</td>
    </tr>
    <tr>
      <th>199</th>
      <td>-1</td>
      <td>74</td>
      <td>volvo</td>
      <td>gas</td>
      <td>turbo</td>
      <td>four</td>
      <td>wagon</td>
      <td>rwd</td>
      <td>front</td>
      <td>104.3</td>
      <td>...</td>
      <td>130</td>
      <td>mpfi</td>
      <td>3.62</td>
      <td>3.15</td>
      <td>7.5</td>
      <td>162</td>
      <td>5100</td>
      <td>17</td>
      <td>22</td>
      <td>18950</td>
    </tr>
    <tr>
      <th>200</th>
      <td>-1</td>
      <td>95</td>
      <td>volvo</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>rwd</td>
      <td>front</td>
      <td>109.1</td>
      <td>...</td>
      <td>141</td>
      <td>mpfi</td>
      <td>3.78</td>
      <td>3.15</td>
      <td>9.5</td>
      <td>114</td>
      <td>5400</td>
      <td>23</td>
      <td>28</td>
      <td>16845</td>
    </tr>
    <tr>
      <th>201</th>
      <td>-1</td>
      <td>95</td>
      <td>volvo</td>
      <td>gas</td>
      <td>turbo</td>
      <td>four</td>
      <td>sedan</td>
      <td>rwd</td>
      <td>front</td>
      <td>109.1</td>
      <td>...</td>
      <td>141</td>
      <td>mpfi</td>
      <td>3.78</td>
      <td>3.15</td>
      <td>8.7</td>
      <td>160</td>
      <td>5300</td>
      <td>19</td>
      <td>25</td>
      <td>19045</td>
    </tr>
    <tr>
      <th>202</th>
      <td>-1</td>
      <td>95</td>
      <td>volvo</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>rwd</td>
      <td>front</td>
      <td>109.1</td>
      <td>...</td>
      <td>173</td>
      <td>mpfi</td>
      <td>3.58</td>
      <td>2.87</td>
      <td>8.8</td>
      <td>134</td>
      <td>5500</td>
      <td>18</td>
      <td>23</td>
      <td>21485</td>
    </tr>
    <tr>
      <th>203</th>
      <td>-1</td>
      <td>95</td>
      <td>volvo</td>
      <td>diesel</td>
      <td>turbo</td>
      <td>four</td>
      <td>sedan</td>
      <td>rwd</td>
      <td>front</td>
      <td>109.1</td>
      <td>...</td>
      <td>145</td>
      <td>idi</td>
      <td>3.01</td>
      <td>3.40</td>
      <td>23.0</td>
      <td>106</td>
      <td>4800</td>
      <td>26</td>
      <td>27</td>
      <td>22470</td>
    </tr>
    <tr>
      <th>204</th>
      <td>-1</td>
      <td>95</td>
      <td>volvo</td>
      <td>gas</td>
      <td>turbo</td>
      <td>four</td>
      <td>sedan</td>
      <td>rwd</td>
      <td>front</td>
      <td>109.1</td>
      <td>...</td>
      <td>141</td>
      <td>mpfi</td>
      <td>3.78</td>
      <td>3.15</td>
      <td>9.5</td>
      <td>114</td>
      <td>5400</td>
      <td>19</td>
      <td>25</td>
      <td>22625</td>
    </tr>
  </tbody>
</table>
<p>10 rows × 26 columns</p>
</div>



<div class="alert alert-danger alertdanger" style="margin-top: 20px">
<h1> Question #1 Answer: </h1>
<b>Run the code below for the solution!</b>
</div>


Double-click <b>here</b> for the solution.

<!-- The answer is below:

print("The last 10 rows of the dataframe\n")
df.tail(10)

-->


<h3>Add Headers</h3>
<p>
Take a look at our dataset; pandas automatically set the header by an integer from 0.
</p>
<p>
To better describe our data we can introduce a header, this information is available at:  <a href="https://archive.ics.uci.edu/ml/datasets/Automobile" target="_blank">https://archive.ics.uci.edu/ml/datasets/Automobile</a>
</p>
<p>
Thus, we have to add headers manually.
</p>
<p>
Firstly, we create a list "headers" that include all column names in order.
Then, we use <code>dataframe.columns = headers</code> to replace the headers by the list we created.
</p>



```python
# create headers list
headers = ["symboling","normalized-losses","make","fuel-type","aspiration", "num-of-doors","body-style",
         "drive-wheels","engine-location","wheel-base", "length","width","height","curb-weight","engine-type",
         "num-of-cylinders", "engine-size","fuel-system","bore","stroke","compression-ratio","horsepower",
         "peak-rpm","city-mpg","highway-mpg","price"]
print("headers\n", headers)
```

    headers
     ['symboling', 'normalized-losses', 'make', 'fuel-type', 'aspiration', 'num-of-doors', 'body-style', 'drive-wheels', 'engine-location', 'wheel-base', 'length', 'width', 'height', 'curb-weight', 'engine-type', 'num-of-cylinders', 'engine-size', 'fuel-system', 'bore', 'stroke', 'compression-ratio', 'horsepower', 'peak-rpm', 'city-mpg', 'highway-mpg', 'price']


 We replace headers and recheck our data frame



```python
df.columns = headers
df.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>symboling</th>
      <th>normalized-losses</th>
      <th>make</th>
      <th>fuel-type</th>
      <th>aspiration</th>
      <th>num-of-doors</th>
      <th>body-style</th>
      <th>drive-wheels</th>
      <th>engine-location</th>
      <th>wheel-base</th>
      <th>...</th>
      <th>engine-size</th>
      <th>fuel-system</th>
      <th>bore</th>
      <th>stroke</th>
      <th>compression-ratio</th>
      <th>horsepower</th>
      <th>peak-rpm</th>
      <th>city-mpg</th>
      <th>highway-mpg</th>
      <th>price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3</td>
      <td>?</td>
      <td>alfa-romero</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>convertible</td>
      <td>rwd</td>
      <td>front</td>
      <td>88.6</td>
      <td>...</td>
      <td>130</td>
      <td>mpfi</td>
      <td>3.47</td>
      <td>2.68</td>
      <td>9.0</td>
      <td>111</td>
      <td>5000</td>
      <td>21</td>
      <td>27</td>
      <td>13495</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>?</td>
      <td>alfa-romero</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>convertible</td>
      <td>rwd</td>
      <td>front</td>
      <td>88.6</td>
      <td>...</td>
      <td>130</td>
      <td>mpfi</td>
      <td>3.47</td>
      <td>2.68</td>
      <td>9.0</td>
      <td>111</td>
      <td>5000</td>
      <td>21</td>
      <td>27</td>
      <td>16500</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>?</td>
      <td>alfa-romero</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>hatchback</td>
      <td>rwd</td>
      <td>front</td>
      <td>94.5</td>
      <td>...</td>
      <td>152</td>
      <td>mpfi</td>
      <td>2.68</td>
      <td>3.47</td>
      <td>9.0</td>
      <td>154</td>
      <td>5000</td>
      <td>19</td>
      <td>26</td>
      <td>16500</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>164</td>
      <td>audi</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>fwd</td>
      <td>front</td>
      <td>99.8</td>
      <td>...</td>
      <td>109</td>
      <td>mpfi</td>
      <td>3.19</td>
      <td>3.40</td>
      <td>10.0</td>
      <td>102</td>
      <td>5500</td>
      <td>24</td>
      <td>30</td>
      <td>13950</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>164</td>
      <td>audi</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>4wd</td>
      <td>front</td>
      <td>99.4</td>
      <td>...</td>
      <td>136</td>
      <td>mpfi</td>
      <td>3.19</td>
      <td>3.40</td>
      <td>8.0</td>
      <td>115</td>
      <td>5500</td>
      <td>18</td>
      <td>22</td>
      <td>17450</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2</td>
      <td>?</td>
      <td>audi</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>sedan</td>
      <td>fwd</td>
      <td>front</td>
      <td>99.8</td>
      <td>...</td>
      <td>136</td>
      <td>mpfi</td>
      <td>3.19</td>
      <td>3.40</td>
      <td>8.5</td>
      <td>110</td>
      <td>5500</td>
      <td>19</td>
      <td>25</td>
      <td>15250</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1</td>
      <td>158</td>
      <td>audi</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>fwd</td>
      <td>front</td>
      <td>105.8</td>
      <td>...</td>
      <td>136</td>
      <td>mpfi</td>
      <td>3.19</td>
      <td>3.40</td>
      <td>8.5</td>
      <td>110</td>
      <td>5500</td>
      <td>19</td>
      <td>25</td>
      <td>17710</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1</td>
      <td>?</td>
      <td>audi</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>wagon</td>
      <td>fwd</td>
      <td>front</td>
      <td>105.8</td>
      <td>...</td>
      <td>136</td>
      <td>mpfi</td>
      <td>3.19</td>
      <td>3.40</td>
      <td>8.5</td>
      <td>110</td>
      <td>5500</td>
      <td>19</td>
      <td>25</td>
      <td>18920</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1</td>
      <td>158</td>
      <td>audi</td>
      <td>gas</td>
      <td>turbo</td>
      <td>four</td>
      <td>sedan</td>
      <td>fwd</td>
      <td>front</td>
      <td>105.8</td>
      <td>...</td>
      <td>131</td>
      <td>mpfi</td>
      <td>3.13</td>
      <td>3.40</td>
      <td>8.3</td>
      <td>140</td>
      <td>5500</td>
      <td>17</td>
      <td>20</td>
      <td>23875</td>
    </tr>
    <tr>
      <th>9</th>
      <td>0</td>
      <td>?</td>
      <td>audi</td>
      <td>gas</td>
      <td>turbo</td>
      <td>two</td>
      <td>hatchback</td>
      <td>4wd</td>
      <td>front</td>
      <td>99.5</td>
      <td>...</td>
      <td>131</td>
      <td>mpfi</td>
      <td>3.13</td>
      <td>3.40</td>
      <td>7.0</td>
      <td>160</td>
      <td>5500</td>
      <td>16</td>
      <td>22</td>
      <td>?</td>
    </tr>
  </tbody>
</table>
<p>10 rows × 26 columns</p>
</div>



we need to replace the "?" symbol with NaN so the dropna() can remove the missing values 



```python
df1=df.replace('?',np.NaN)

```

we can drop missing values along the column "price" as follows  



```python
df=df1.dropna(subset=["price"], axis=0)
df.head(20)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>symboling</th>
      <th>normalized-losses</th>
      <th>make</th>
      <th>fuel-type</th>
      <th>aspiration</th>
      <th>num-of-doors</th>
      <th>body-style</th>
      <th>drive-wheels</th>
      <th>engine-location</th>
      <th>wheel-base</th>
      <th>...</th>
      <th>engine-size</th>
      <th>fuel-system</th>
      <th>bore</th>
      <th>stroke</th>
      <th>compression-ratio</th>
      <th>horsepower</th>
      <th>peak-rpm</th>
      <th>city-mpg</th>
      <th>highway-mpg</th>
      <th>price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3</td>
      <td>NaN</td>
      <td>alfa-romero</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>convertible</td>
      <td>rwd</td>
      <td>front</td>
      <td>88.6</td>
      <td>...</td>
      <td>130</td>
      <td>mpfi</td>
      <td>3.47</td>
      <td>2.68</td>
      <td>9.0</td>
      <td>111</td>
      <td>5000</td>
      <td>21</td>
      <td>27</td>
      <td>13495</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>NaN</td>
      <td>alfa-romero</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>convertible</td>
      <td>rwd</td>
      <td>front</td>
      <td>88.6</td>
      <td>...</td>
      <td>130</td>
      <td>mpfi</td>
      <td>3.47</td>
      <td>2.68</td>
      <td>9.0</td>
      <td>111</td>
      <td>5000</td>
      <td>21</td>
      <td>27</td>
      <td>16500</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>NaN</td>
      <td>alfa-romero</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>hatchback</td>
      <td>rwd</td>
      <td>front</td>
      <td>94.5</td>
      <td>...</td>
      <td>152</td>
      <td>mpfi</td>
      <td>2.68</td>
      <td>3.47</td>
      <td>9.0</td>
      <td>154</td>
      <td>5000</td>
      <td>19</td>
      <td>26</td>
      <td>16500</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>164</td>
      <td>audi</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>fwd</td>
      <td>front</td>
      <td>99.8</td>
      <td>...</td>
      <td>109</td>
      <td>mpfi</td>
      <td>3.19</td>
      <td>3.40</td>
      <td>10.0</td>
      <td>102</td>
      <td>5500</td>
      <td>24</td>
      <td>30</td>
      <td>13950</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>164</td>
      <td>audi</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>4wd</td>
      <td>front</td>
      <td>99.4</td>
      <td>...</td>
      <td>136</td>
      <td>mpfi</td>
      <td>3.19</td>
      <td>3.40</td>
      <td>8.0</td>
      <td>115</td>
      <td>5500</td>
      <td>18</td>
      <td>22</td>
      <td>17450</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2</td>
      <td>NaN</td>
      <td>audi</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>sedan</td>
      <td>fwd</td>
      <td>front</td>
      <td>99.8</td>
      <td>...</td>
      <td>136</td>
      <td>mpfi</td>
      <td>3.19</td>
      <td>3.40</td>
      <td>8.5</td>
      <td>110</td>
      <td>5500</td>
      <td>19</td>
      <td>25</td>
      <td>15250</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1</td>
      <td>158</td>
      <td>audi</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>fwd</td>
      <td>front</td>
      <td>105.8</td>
      <td>...</td>
      <td>136</td>
      <td>mpfi</td>
      <td>3.19</td>
      <td>3.40</td>
      <td>8.5</td>
      <td>110</td>
      <td>5500</td>
      <td>19</td>
      <td>25</td>
      <td>17710</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1</td>
      <td>NaN</td>
      <td>audi</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>wagon</td>
      <td>fwd</td>
      <td>front</td>
      <td>105.8</td>
      <td>...</td>
      <td>136</td>
      <td>mpfi</td>
      <td>3.19</td>
      <td>3.40</td>
      <td>8.5</td>
      <td>110</td>
      <td>5500</td>
      <td>19</td>
      <td>25</td>
      <td>18920</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1</td>
      <td>158</td>
      <td>audi</td>
      <td>gas</td>
      <td>turbo</td>
      <td>four</td>
      <td>sedan</td>
      <td>fwd</td>
      <td>front</td>
      <td>105.8</td>
      <td>...</td>
      <td>131</td>
      <td>mpfi</td>
      <td>3.13</td>
      <td>3.40</td>
      <td>8.3</td>
      <td>140</td>
      <td>5500</td>
      <td>17</td>
      <td>20</td>
      <td>23875</td>
    </tr>
    <tr>
      <th>10</th>
      <td>2</td>
      <td>192</td>
      <td>bmw</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>sedan</td>
      <td>rwd</td>
      <td>front</td>
      <td>101.2</td>
      <td>...</td>
      <td>108</td>
      <td>mpfi</td>
      <td>3.50</td>
      <td>2.80</td>
      <td>8.8</td>
      <td>101</td>
      <td>5800</td>
      <td>23</td>
      <td>29</td>
      <td>16430</td>
    </tr>
    <tr>
      <th>11</th>
      <td>0</td>
      <td>192</td>
      <td>bmw</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>rwd</td>
      <td>front</td>
      <td>101.2</td>
      <td>...</td>
      <td>108</td>
      <td>mpfi</td>
      <td>3.50</td>
      <td>2.80</td>
      <td>8.8</td>
      <td>101</td>
      <td>5800</td>
      <td>23</td>
      <td>29</td>
      <td>16925</td>
    </tr>
    <tr>
      <th>12</th>
      <td>0</td>
      <td>188</td>
      <td>bmw</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>sedan</td>
      <td>rwd</td>
      <td>front</td>
      <td>101.2</td>
      <td>...</td>
      <td>164</td>
      <td>mpfi</td>
      <td>3.31</td>
      <td>3.19</td>
      <td>9.0</td>
      <td>121</td>
      <td>4250</td>
      <td>21</td>
      <td>28</td>
      <td>20970</td>
    </tr>
    <tr>
      <th>13</th>
      <td>0</td>
      <td>188</td>
      <td>bmw</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>rwd</td>
      <td>front</td>
      <td>101.2</td>
      <td>...</td>
      <td>164</td>
      <td>mpfi</td>
      <td>3.31</td>
      <td>3.19</td>
      <td>9.0</td>
      <td>121</td>
      <td>4250</td>
      <td>21</td>
      <td>28</td>
      <td>21105</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1</td>
      <td>NaN</td>
      <td>bmw</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>rwd</td>
      <td>front</td>
      <td>103.5</td>
      <td>...</td>
      <td>164</td>
      <td>mpfi</td>
      <td>3.31</td>
      <td>3.19</td>
      <td>9.0</td>
      <td>121</td>
      <td>4250</td>
      <td>20</td>
      <td>25</td>
      <td>24565</td>
    </tr>
    <tr>
      <th>15</th>
      <td>0</td>
      <td>NaN</td>
      <td>bmw</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>rwd</td>
      <td>front</td>
      <td>103.5</td>
      <td>...</td>
      <td>209</td>
      <td>mpfi</td>
      <td>3.62</td>
      <td>3.39</td>
      <td>8.0</td>
      <td>182</td>
      <td>5400</td>
      <td>16</td>
      <td>22</td>
      <td>30760</td>
    </tr>
    <tr>
      <th>16</th>
      <td>0</td>
      <td>NaN</td>
      <td>bmw</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>sedan</td>
      <td>rwd</td>
      <td>front</td>
      <td>103.5</td>
      <td>...</td>
      <td>209</td>
      <td>mpfi</td>
      <td>3.62</td>
      <td>3.39</td>
      <td>8.0</td>
      <td>182</td>
      <td>5400</td>
      <td>16</td>
      <td>22</td>
      <td>41315</td>
    </tr>
    <tr>
      <th>17</th>
      <td>0</td>
      <td>NaN</td>
      <td>bmw</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>rwd</td>
      <td>front</td>
      <td>110.0</td>
      <td>...</td>
      <td>209</td>
      <td>mpfi</td>
      <td>3.62</td>
      <td>3.39</td>
      <td>8.0</td>
      <td>182</td>
      <td>5400</td>
      <td>15</td>
      <td>20</td>
      <td>36880</td>
    </tr>
    <tr>
      <th>18</th>
      <td>2</td>
      <td>121</td>
      <td>chevrolet</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>hatchback</td>
      <td>fwd</td>
      <td>front</td>
      <td>88.4</td>
      <td>...</td>
      <td>61</td>
      <td>2bbl</td>
      <td>2.91</td>
      <td>3.03</td>
      <td>9.5</td>
      <td>48</td>
      <td>5100</td>
      <td>47</td>
      <td>53</td>
      <td>5151</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1</td>
      <td>98</td>
      <td>chevrolet</td>
      <td>gas</td>
      <td>std</td>
      <td>two</td>
      <td>hatchback</td>
      <td>fwd</td>
      <td>front</td>
      <td>94.5</td>
      <td>...</td>
      <td>90</td>
      <td>2bbl</td>
      <td>3.03</td>
      <td>3.11</td>
      <td>9.6</td>
      <td>70</td>
      <td>5400</td>
      <td>38</td>
      <td>43</td>
      <td>6295</td>
    </tr>
    <tr>
      <th>20</th>
      <td>0</td>
      <td>81</td>
      <td>chevrolet</td>
      <td>gas</td>
      <td>std</td>
      <td>four</td>
      <td>sedan</td>
      <td>fwd</td>
      <td>front</td>
      <td>94.5</td>
      <td>...</td>
      <td>90</td>
      <td>2bbl</td>
      <td>3.03</td>
      <td>3.11</td>
      <td>9.6</td>
      <td>70</td>
      <td>5400</td>
      <td>38</td>
      <td>43</td>
      <td>6575</td>
    </tr>
  </tbody>
</table>
<p>20 rows × 26 columns</p>
</div>



Now, we have successfully read the raw dataset and add the correct headers into the data frame.


 <div class="alert alert-danger alertdanger" style="margin-top: 20px">
<h1> Question #2: </h1>
<b>Find the name of the columns of the dataframe</b>
</div>



```python
# Write your code below and press Shift+Enter to execute
print(df.columns)
```

    Index(['symboling', 'normalized-losses', 'make', 'fuel-type', 'aspiration',
           'num-of-doors', 'body-style', 'drive-wheels', 'engine-location',
           'wheel-base', 'length', 'width', 'height', 'curb-weight', 'engine-type',
           'num-of-cylinders', 'engine-size', 'fuel-system', 'bore', 'stroke',
           'compression-ratio', 'horsepower', 'peak-rpm', 'city-mpg',
           'highway-mpg', 'price'],
          dtype='object')


Double-click <b>here</b> for the solution.

<!-- The answer is below:

print(df.columns)

-->


<h2>Save Dataset</h2>
<p>
Correspondingly, Pandas enables us to save the dataset to csv  by using the <code>dataframe.to_csv()</code> method, you can add the file path and name along with quotation marks in the brackets.
</p>
<p>
    For example, if you would save the dataframe <b>df</b> as <b>automobile.csv</b> to your local machine, you may use the syntax below:
</p>

df.to_csv("automobile.csv", index=False)
 We can also read and save other file formats, we can use similar functions to **`pd.read_csv()`** and **`df.to_csv()`** for other data formats, the functions are listed in the following table:


<h2>Read/Save Other Data Formats</h2>

| Data Formate |        Read       |            Save |
| ------------ | :---------------: | --------------: |
| csv          |  `pd.read_csv()`  |   `df.to_csv()` |
| json         |  `pd.read_json()` |  `df.to_json()` |
| excel        | `pd.read_excel()` | `df.to_excel()` |
| hdf          |  `pd.read_hdf()`  |   `df.to_hdf()` |
| sql          |  `pd.read_sql()`  |   `df.to_sql()` |
| ...          |        ...        |             ... |


<h1 id="basic_insight">Basic Insight of Dataset</h1>
<p>
After reading data into Pandas dataframe, it is time for us to explore the dataset.<br>
There are several ways to obtain essential insights of the data to help us better understand our dataset.
</p>


<h2>Data Types</h2>
<p>
Data has a variety of types.<br>
The main types stored in Pandas dataframes are <b>object</b>, <b>float</b>, <b>int</b>, <b>bool</b> and <b>datetime64</b>. In order to better learn about each attribute, it is always good for us to know the data type of each column. In Pandas: <code>dtypes</code> returns a Series with the data type of each column.
</p>



```python
# check the data type of data frame "df" by .dtypes
print(df.dtypes)
```

    symboling              int64
    normalized-losses     object
    make                  object
    fuel-type             object
    aspiration            object
    num-of-doors          object
    body-style            object
    drive-wheels          object
    engine-location       object
    wheel-base           float64
    length               float64
    width                float64
    height               float64
    curb-weight            int64
    engine-type           object
    num-of-cylinders      object
    engine-size            int64
    fuel-system           object
    bore                  object
    stroke                object
    compression-ratio    float64
    horsepower            object
    peak-rpm              object
    city-mpg               int64
    highway-mpg            int64
    price                 object
    dtype: object


<p>
As a result, as shown above, it is clear to see that the data type of "symboling" and "curb-weight" are <code>int64</code>, "normalized-losses" is <code>object</code>, and "wheel-base" is <code>float64</code>, etc.
</p>
<p>
These data types can be changed; If you want to learn more about data types or need more preparation before starting this course please visit:
    <li>Coursera: <a href="https://www.coursera.org/learn/data-analysis-with-python#syllabus" target="_blank">https://www.coursera.org/learn/data-analysis-with-python#syllabus
</a></li>
    <li>CC.ai: <a href="https://cognitiveclass.ai/courses/data-analysis-python" target="_blank">https://cognitiveclass.ai/courses/data-analysis-python</a></li>
</p>


<h2>Describe</h2>
If we would like to get a statistical summary of each column, such as count, column mean value, column standard deviation, etc. We use the describe method:

dataframe.describe()
This method will provide various summary statistics, excluding <code>NaN</code> (Not a Number) values.



```python
df.describe()
```

<p>
This shows the statistical summary of all numeric-typed (int, float) columns.<br>
For example, the attribute "symboling" has 205 counts, the mean value of this column is 0.83, the standard deviation is 1.25, the minimum value is -2, 25th percentile is 0, 50th percentile is 1, 75th percentile is 2, and the maximum value is 3.
<br>
However, what if we would also like to check all the columns including those that are of type object.
<br><br>

You can add an argument <code>include = "all"</code> inside the bracket. Let's try it again.

</p>



```python
# describe all the columns in "df" 
df.describe(include = "all")
```

<p>
Now, it provides the statistical summary of all the columns, including object-typed attributes.<br>
We can now see how many unique values, which is the top value and the frequency of top value in the object-typed columns.<br>
Some values in the table above show as "NaN", this is because those numbers are not available regarding a particular column type.<br>
</p>


<div class="alert alert-danger alertdanger" style="margin-top: 20px">
<h1> Question #3: </h1>

<p>
You can select the columns of a data frame by indicating the name of  each column, for example, you can select the three columns as follows:
</p>
<p>
    <code>dataframe[['column 1', 'column 2', 'column 3']]</code>
</p>
<p>
Where "column" is the name of the column, you can apply the method  ".describe()" to get the statistics of those columns as follows:
</p>
<p>
    <code>dataframe[['column 1', 'column 2', 'column 3']].describe()</code>
</p>

Apply the  method to ".describe()" to the columns 'length' and 'compression-ratio'.

</div>



```python
# Write your code below and press Shift+Enter to execute 
df[["length", "compression-ratio"]].describe
```




    <bound method NDFrame.describe of      length  compression-ratio
    0     168.8                9.0
    1     168.8                9.0
    2     171.2                9.0
    3     176.6               10.0
    4     176.6                8.0
    ..      ...                ...
    200   188.8                9.5
    201   188.8                8.7
    202   188.8                8.8
    203   188.8               23.0
    204   188.8                9.5
    
    [201 rows x 2 columns]>



Double-click <b>here</b> for the solution.

<!-- The answer is below:

df[['length', 'compression-ratio']].describe()

-->


<h2>Info</h2>
Another method you can use to check your dataset is:

dataframe.info()
It provide a concise summary of your DataFrame. 

This method prints information about a DataFrame including the index dtype and columns, non-null values and memory usage.



```python
# look at the info of "df"
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 201 entries, 0 to 204
    Data columns (total 26 columns):
     #   Column             Non-Null Count  Dtype  
    ---  ------             --------------  -----  
     0   symboling          201 non-null    int64  
     1   normalized-losses  164 non-null    object 
     2   make               201 non-null    object 
     3   fuel-type          201 non-null    object 
     4   aspiration         201 non-null    object 
     5   num-of-doors       199 non-null    object 
     6   body-style         201 non-null    object 
     7   drive-wheels       201 non-null    object 
     8   engine-location    201 non-null    object 
     9   wheel-base         201 non-null    float64
     10  length             201 non-null    float64
     11  width              201 non-null    float64
     12  height             201 non-null    float64
     13  curb-weight        201 non-null    int64  
     14  engine-type        201 non-null    object 
     15  num-of-cylinders   201 non-null    object 
     16  engine-size        201 non-null    int64  
     17  fuel-system        201 non-null    object 
     18  bore               197 non-null    object 
     19  stroke             197 non-null    object 
     20  compression-ratio  201 non-null    float64
     21  horsepower         199 non-null    object 
     22  peak-rpm           199 non-null    object 
     23  city-mpg           201 non-null    int64  
     24  highway-mpg        201 non-null    int64  
     25  price              201 non-null    object 
    dtypes: float64(5), int64(5), object(16)
    memory usage: 42.4+ KB


<h1>Excellent! You have just completed the  Introduction  Notebook!</h1>


### Thank you for completing this lab!

## Author

<a href="https://www.linkedin.com/in/joseph-s-50398b136/" target="_blank">Joseph Santarcangelo</a>

### Other Contributors

<a href="https://www.linkedin.com/in/mahdi-noorian-58219234/" target="_blank">Mahdi Noorian PhD</a>

Bahare Talayian

Eric Xiao

Steven Dong

Parizad

Hima Vasudevan

<a href="https://www.linkedin.com/in/fiorellawever/" target="_blank">Fiorella Wenver</a>

<a href=" https://www.linkedin.com/in/yi-leng-yao-84451275/ " target="_blank" >Yi Yao</a>.

## Change Log

| Date (YYYY-MM-DD) | Version | Changed By | Change Description                       |
| ----------------- | ------- | ---------- | ---------------------------------------- |
| 2020-10-06        | 2.3     | Aije       | Added links to coursera and cc.ai        |
| 2020-09-22        | 2.2     | Nayef      | Added replace() method to remove '?'     |
| 2020-09-09        | 2.1     | Lakshmi    | Made changes in info method of dataframe |
| 2020-08-27        | 2.0     | Lavanya    | Moved lab to course repo in GitLab       |

<hr>

## <h3 align="center"> © IBM Corporation 2020. All rights reserved. <h3/>



```python

```
