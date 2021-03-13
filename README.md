# Election_Analysis

## Project Overview
A Colorado Board of Elections employee has tasked you with completing the election audit of a recent local congressional election. He has asked for five items specifically:

1. The total number of votes cast.
2. A complete list of candidates who received votes.
3. The percentage of votes each candidate won.
4. The total number of votes each candidate won.
5. The winner of the election based on popular vote.

## Resources
- Data Source: election_results.csv
- Software: Python 3.8.5, Visual Studio Code 1.54.1

## Summary
The analysis of the election show that:
- There were 369,711 votes cast in the election.
- The candidates were:
  - Charles Casper Stockham
  - Diana DeGette
  - Raymon Anthony Doane
- The candidate results were:
  - Charles Casper Stockham received 23.0% of the vote and 85,213 total votes.
  - Diana DeGette received 73.8% of the vote and 272,892 total votes.
  - Raymon Anthony Doane received 3.1% of the vote and 11,606 total votes.
- The winner of the election was:
  - Diana DeGette, who received 73.8% of the vote and 272,892 total votes.

## Challenge Overview: Election Audit
### Purpose of Election Audit
The Colorado Board of Elections has asked for more information on the individual county turnout specifcially to be included in the analysis. They would like to know the following:

1. The voter turnout for each county.
2. The percentage of votes from each county out of the total count.
3. The county with the highest turnout.

### Results of Election Audit
- How many votes were cast in this congressional election?
  - There were 369,711 total votes cast in this congressional election.
  - See line 45 in the script. As we loop through each row in the file, we add to the variable `total_votes`.
  ```
  # Add to the total vote count
        total_votes = total_votes + 1
  ```
- Provide a breakdown of the number of votes and the percentage of total votes for each county in the precinct.
  - Jefferson County cast 38,855 votes, accounting for 10.5% of the total votes cast.
  - Denver County cast 306,055 votes, accounting for 82.8% of the total votes cast.
  - Arapahoe County cast 24,801 votes, accounting for 6.7% of the total votes cast.
  - The process to get these results can be found on line 68 and 97 in the script.
  ```
  for county_name in county_votes:
        # 6b: Retrieve the county vote count.
        vote_count = county_votes[county_name]
        # 6c: Calculate the percentage of votes for the county.
        percentage_county = float(vote_count) / float(total_votes) * 100
  ```
- Which county had the largest number of votes?
  - Denver had the largest voter turnout.
  - We compare the county's vote count to voter turnout in line 106.
  ```
  if (vote_count > voter_turnout):
            largest_county = county_name
            voter_turnout = vote_count
  ```
- Provide a breakdown of the number of votes and the percentage of the total votes each candidate received.
  - Charles Casper Stockham received 85,213 votes, or 23% of the total votes cast.
  - Diana DeGette received 272,892 votes, or 82.8% of the total votes cast.
  - Raymon Anthony Doane received 11,606 votes, or 3.1% of the total votes cast.
  - As we loop through the rows, we collect candidate names and add up their votes. See line 55 and 125 for these steps.
  ```
  if candidate_name not in candidate_options:

            # Add the candidate name to the candidate list.
            candidate_options.append(candidate_name)

            # And begin tracking that candidate's voter count.
            candidate_votes[candidate_name] = 0

        # Add a vote to that candidate's count
        candidate_votes[candidate_name] += 1
  ```
- Which candidate won the election, what was their vote count, and what was their percentage of the total votes?
  - Diana DeGette won the election. She received 272,892 votes, or 82.8% of all the votes.
  - See line 137 for this step.
  ```
  if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage
  ```

## Challenge Summary
The script used in this audit can be easily applied to any election. For example, next year, the election committee can get the same kind of information just by linking an updated file to the script.
```
file_to_load = os.path.join("Resources", "election_results.csv")
```
Use the current year's election results file in place of `election_results.csv`.

This script could be improved by creating a function to calculate and format percentages and total votes. Seeing as this process is repeated throughout the script, consolidating it to a function so it doesn't have to be written out every time will make the code easier to read and understand. 
