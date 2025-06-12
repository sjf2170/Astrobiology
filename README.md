# Astrobiology
Includes Earth Similarity Index Calculator and Optimal Path Algorithm

In 2022, as a part of Columbia's Summer Undergraduate Research Experience in Math Modeling Program, I created this Jupyter Notebook, ESI.ipynb to help me solve the question of "If we could travel to Exoplanets, what would be the optimal path to take to do so to maximize results and minimize cost (assuming constant cost per lightyear)?"

The data was sourced from NASA's exoplanet catalogue, and using an excel spreadsheet, this data was converted into a few key parameters: Name of Star System, Name of Exoplanet, Spherical Coordinates (for location), and Earth Similarity Index (ESI).  Earth has a 1.0 ESI and Mars has a 0.7 ESI (Schulze-Makuch et al., 2011).  This excel sheet was converted to CSV and is listed as 'Exoplanets.csv.'  

The Jupyter Notebook begins by the CSV file and converting ESI into a value deemed "Reward."  "Reward" is a function that increases as Earth Similarity increases.  Planets in the same star system have their rewards totalled through additively.  The reward for visiting earth from another planet is 0 as it is not exploratory.  To determine whether a star system is deemed "worth" visiting, the distance (in units of light-years) is subtracted from the reward to get the "score."

The next function plots extrasolar star systems in space with their size proportional to their "Reward" value.  Earth is plotted in green at (0,0,0).

The p_dists.csv represents graphed edges between two star systems, and is nearly symmetric, however all of the return to earth trips are replaced with a large cost, so that the path is linear and not a cycle.

The next section is a model based off ant colony exploration.  This function solves the traveling salesman problem, and chooses the optimal route for a probe that visits all of the exoplanets with an ESI higher than Mars (0.70).  It is not an analytic solution, and occasionally provides suboptimal results, but we have found that its results are largely correct for this sample size.

The next section plots this shortest-distance path between all planets.  The arrows show the direction of travel, which begins at Earth

The next function outputs the matrices for Reward, Pairwise Distances, and Score, which can be seen in their respective csv files.

The final function combines high-scoring blocks to find the highest-scoring path.  The final, highest-scoring trip only included 2 star systems: TRAPPIST-1 and GJ 273.  TRAPPIST-1 is the highest reward star-system, with 6 planets with an ESI over .70 and two of the top 3 highest ESI planets (TRAPPIST-1 d and TRAPPIST-1 e).  GJ 273 had the second highest ESI planet and was the closest star system.
