# Comparative Bioinformatics Pipeline: GC-Content Shifts in M. tuberculosis

This is a local bioinformatics project I built during my 2nd year of B.Tech Biotechnology. The pipeline automates reading real genetic data from NCBI, processes it to look for changes, calculates group statistics, and visualizes genomic differences between drug-sensitive and drug-resistant bacterial strains.

---

##  1. The Biology: Why Does This Matter?
* **The Organism:** *Mycobacterium tuberculosis* is the bacterium that causes Tuberculosis (TB). It is a globally dangerous pathogen and biologically unique because its DNA naturally contains a very high amount of Guanine (G) and Cytosine (C) letters compared to other bacteria.
* **The Problem (AMR):** This bacterium is rapidly evolving **Antimicrobial Resistance (AMR)**, meaning our current medicines are stopping working against it. 
* **The Target Gene:** I chose to look specifically at the **katG gene**. This gene is responsible for creating an enzyme that activates a primary anti-TB drug called **Isoniazid**. When the bacteria mutates this specific gene, the drug becomes useless.
* **The GC Hypothesis:** G and C bases stick together using **three hydrogen bonds**, while A and T bases only use two. Because of this, higher GC-content makes the DNA physically stronger. I wanted to see if bacteria mutating under antibiotic stress show a shift towards higher GC-content to protect their genome.

---

##  2. What I Did in This Project
Instead of opening files and counting thousands of DNA letters manually with my eyes, I built an automated Python pipeline that executes four core stages:

1. **Cleaned Raw NCBI Data:** The pipeline opens the raw `.fna` file downloaded from NCBI Datasets. It skips the top title/header line (the line starting with `>`), cleans up hidden spacing breaks, and converts all sequence text into clean uppercase characters.
2. **Built a Counting Engine:** It scans through the gene line-by-line using a loop to count the individual `G` and `C` letters, calculating the baseline reference length and GC percentage.
3. **Simulated Clinical Strain Cohorts:** To model evolution without manually managing dozens of separate large files, I wrote logic loops to generate two distinct study groups: a drug-sensitive group (with minimal natural genetic drift) and a drug-resistant group (with heavy structural mutations).
4. **Calculated Comparative Statistics:** The code aggregates the results into lists, calculates the mathematical average (mean) for both cohorts, and subtracts them to quantify the exact genomic shift.
5. **Auto-Generated the Final Chart:** The pipeline maps the statistical averages onto a clean, zoomed-in visual bar graph to instantly show the final comparison.

---

##  Our Results
* **Total Length of katG Gene:** 2,223 base pairs
* **Total G and C bases found:** 1,436 bases
* **Average GC % of Sensitive Strains:** 64.69%
* **Average GC % of Resistant Strains:** 66.40%
* **Observed Genomic Shift:** +1.71% (The mutated strains show a clear upward shift in GC density).
* ![M. tuberculosis GC-Content Shift Graph](project_graph.png)


---

##   3. What We Used (The Tech Stack)
* **Data Source:** [NCBI Datasets Repository](https://nih.gov) (Targeting *Mycobacterium tuberculosis* H37Rv *katG* sequence).
* **Development Environment:** **PyCharm Professional IDE** running an isolated local Python virtual environment (`.venv`) on Windows.
* **Programming Logic:** Pure **Python 3**. I used core programming components like standard file I/O operations (`with open`), `for` loops for streaming lines, `if` conditions for string filtration, and standard arithmetic blocks.
* **Graphics Library:** **Matplotlib** (`matplotlib.pyplot`) to style the chart canvas, color code the groups, zoom the axes, and overlay data value stamps on top of the bars.

---

##   Academic Info
* **Author:** Vangmayi muppalla, Second Year Student, B.Tech Biotechnology  
* **Project Type:** Mini-Project / Bioinformatics Practice
