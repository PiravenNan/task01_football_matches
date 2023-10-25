# Football Matches - Tasks

Each of the questions/tasks below can be answered using a `SELECT` query. When you find a solution copy it into the code block under the question before pushing your solution to GitHub.

1) Find all the matches from 2017.

```sql 

<!-- SELECT * FROM Matches WHERE season = 2017;

```

2) Find all the matches featuring Barcelona.

```sql
<!-- SELECT * FROM Matches WHERE LOWER(hometeam) LIKE LOWER('Barcelona') OR LOWER(awayteam) LIKE LOWER('Barcelona');



```

3) What are the names of the Scottish divisions included?

```sql
<!-- SELECT DISTINCT name, country FROM divisions WHERE LOWER(country) LIKE LOWER('scotland')


```

4) Find the value of the `code` for the `Bundesliga` division. Use that code to find out how many matches Freiburg have played in that division. HINT: You will need to query both tables

```sql
<!-- SELECT code FROM divisions WHERE LOWER(name) = LOWER('Bundesliga'); {D1}
<!-- SELECT division_code, hometeam, awayteam FROM matches WHERE division_code = 'D1' AND (hometeam = 'Freiburg' OR awayteam = 'Freiburg');


```

5)  Find the teams which include the word "City" in their name. HINT: Not every team has been entered into the database with their full name, eg. `Norwich City` are listed as `Norwich`. If your query is correct it should return four teams.

```sql
<!-- SELECT DISTINCT (hometeam) FROM matches WHERE LOWER(hometeam) LIKE '%city' ;


```

6) How many different teams have played in matches recorded in a French division?

```sql
<!-- SELECT COUNT(DISTINCT(hometeam,awayteam)) FROM matches WHERE division_code LIKE 'F%';


```

7) Have Huddersfield played Swansea in any of the recorded matches?

```sql
<!-- SELECT * FROM matches WHERE (awayteam = 'Huddersfield' and hometeam = 'Swansea') OR (hometeam = 'Huddersfield' and awayteam = 'Swansea') ;


```

8) How many draws were there in the `Eredivisie` between 2010 and 2015?

```sql
<!-- SELECT COUNT(*) FROM matches WHERE (fthg = ftag) AND 2010<=season AND season<=2015;


```

9) Select the matches played in the Premier League in order of total goals scored (`fthg` + `ftag`) from highest to lowest. When two matches have the same total the match with more home goals (`fthg`) should come first. 

```sql
<!-- SELECT * , (fthg+ftag) AS total_goals FROM matches WHERE division_code='E0' ORDER BY total_goals DESC, fthg DESC;


```

10) Find the name of the division in which the most goals were scored in a single season and the year in which it happened.

```sql
<!-- SELECT division_code,season ,SUM(fthg+ftag) FROM matches GROUP BY division_code,season ORDER BY SUM DESC LIMIT 1;


```

### Useful Resources

- [Filtering results](https://www.w3schools.com/sql/sql_where.asp)
- [Ordering results](https://www.w3schools.com/sql/sql_orderby.asp)
- [Grouping results](https://www.w3schools.com/sql/sql_groupby.asp)