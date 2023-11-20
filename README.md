# nosql-challenge
Module 12 Challenge
## Part 1 - Database and Jupyter Notebook Set Up ##
The <i>**uk_food**</i> MongoDB database and the <i>**establishments**</i> collection are created by running:<br>
<i>`mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json`</i>
<br>

## Part 2 - Update the Database ##
We will use the Jupiter notebook [<i>**NoSQL_setup_starter.ipynb**</i>](https://github.com/xoffvsg/nosql-challenge/blob/main/NoSQL_setup_starter.ipynb) to update the <i>establishments</i> collection.<br>
After inserting the document corresponding to the new "Penang Flavours" restaurant, we will update its _BusinessTypeID_ with the value "1" to reflect its <i>BusinessType</i> being under the  <i>Restaurant/Cafe/Canteen</i> category.<br>
We will the delete the documents in the <i>establishments</i> collection corresponding to the businesses managed by the Dover authority.<br>
We will the update the database to convert the latitudes and longitudes in all the documents from String to Float, and the ratings from String to Integer.<br>
Note: Using __$toDecimal__ to convert a string to decimal creates a Decimal128 type, which does not allow direct arithmetic operations with floats as required in the second part of the challenge (distances from Lon and Lat). We will use __$toDouble__ instead to convert the strings to floats.<br>

## Part 3 - Exploratory Analysis ##
We will use the Jupiter notebook [<i>**NoSQL_analysis_starter.ipynb**</i>](https://github.com/xoffvsg/nosql-challenge/blob/main/NoSQL_analysis_starter.ipynb) to explore the collection.<br>
We find that 41 establisments in the collection have a hygiene score equal to 20 (the higher the value, the worse the establishment is). The query result is converted to a Pandas dataframe.<br>
We find that 33 establishments managed by the London authority in the collection have a rating greater than or equal to 4 (on a scale of 1-5 with the higher the value, the better the establishment is). The query result is converted to a Pandas dataframe.<br>
There are 87 establishments with a rating value of 5 (the highest) within 0.01 degrees of the "Penang Flavours" restaurant (managed by the Greenwich authority). We sort them by the hygiene score from good to bad, and we randomly select the first 5 establishments with the best hygiene score. The query result is converted to a Pandas dataframe.<br>
<br>
Lastly, we search how many establishments in each Local Authority area have a hygiene score of 0 (the best). We find that the district with the highest number of such establishments is Thanet (see table 1), but Sunderland, Reading, Kensington and Chelsea, Dorset, Broxbourne, and North Norfolk only have one establishment with this rating located in their respective purview... Caveat emptor...
<br><br>


<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>_id</th>
      <th>count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Thanet</td>
      <td>1130</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Greenwich</td>
      <td>882</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Maidstone</td>
      <td>713</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Newham</td>
      <td>711</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Swale</td>
      <td>686</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Chelmsford</td>
      <td>680</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Medway</td>
      <td>672</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Bexley</td>
      <td>607</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Southend-On-Sea</td>
      <td>586</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Tendring</td>
      <td>542</td>
    </tr>
  </tbody>
</table>
</div>
Figure 1



