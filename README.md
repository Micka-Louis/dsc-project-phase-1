# Akademi (Flatiron School) — Data Science & AI, Cohorte 2025  
## First Project-Phase 1  
 **Student Name:** Micka LOUIS  
 **Student Pace:** Self-paced  
 **Submission Deadline:** June 8, 2025  
 **Instructors' Names:** Wedter JEROME & Geovany Batista Polo LAGUERRE  
 **Blog Post URL:** https://github.com/Micka-Louis/dsc-project-phase-1.git  

 #Project Title  
 
##US Aviation Accidents Analysis(1962-2023)   
![Cover](images/image1.webp)  

#Overview  
##This notebook presents a structured analysis of aviation accident data. It follows the CRISP-DM methodology, offering insight into understanding and preparing data for decision-making in aviation safety.  

# Business Understanding    
![Business](images/image3.jpg)  
Aviation safety is essential to public trust and operational efficiency. Understanding past accidents helps stakeholders identify systemic issues and implement safety improvements.  

# Business Problem  

![Cover](images/image2.avif)  
The company is planning to expand into new industries as part of a broader diversification strategy. One of the targeted areas is aviation — specifically, the purchase and operation of aircraft for commercial and private services. However, the company currently lacks knowledge about the aviation industry, particularly regarding the safety and risk profiles of different aircraft.  

The objective is to identify which aircraft models present the lowest operational risk, using historical data on aircraft incidents and accidents. The goal is to provide data-driven insights that will guide the head of the new aviation division in selecting the safest and most reliable aircraft to purchase.  

To support this effort, aviation safety data will be sourced, explored, and analyzed, with the results translated into actionable business recommendations that reduce risk and support informed decision-making in this new venture.  

# Data Understanding    

Our analysis leverages the AviationData from the NTSB (1962-2023), with a focus on the 1982-2023 period to examine modern aviation safety trends. The dataset provides comprehensive attributes including accident context (date, location, aircraft details), safety metrics (injuries, weather conditions), and aircraft specifications (engine type, capacity). We evaluate accident patterns across flight phases, operator types, and geographic regions to identify high-risk scenarios, while the dataset's flexibility allows filtering by time period, injury severity, and aircraft characteristics for tailored insights. This structured approach enables us to uncover key trends, assess risk factors, and ultimately support data-driven safety improvements in aviation operations.  

# Methods  

This project uses descriptive analysis to examine trends in U.S. aviation accidents (2000–2022), including:

Temporal trends (accident/injury rates over time).  
Manufacturer comparisons (accident frequency vs. severity).  
Geographic & weather-related patterns (high-risk states, VMC/IMC conditions).  

The analysis identifies key risk factors and safety improvements, supporting data-driven decision-making for aviation stakeholders.  

# Results
# Clean and standardize the 'Make' column (remove whitespace, convert to uppercase)
df['Make'] = df['Make'].str.strip().str.upper()

# Count accidents per manufacturer and select the 10 with the LOWEST accidents
manufacturer_counts = df['Make'].value_counts()
least_accident_makers = manufacturer_counts.sort_values(ascending=True).head(10)

# Visualization
plt.figure(figsize=(10, 6))
least_accident_makers.plot(kind='barh', color='seagreen')
plt.title('Top 10 Manufacturers with the Lowest Number of Accidents')
plt.xlabel('Number of Accidents')
plt.ylabel('Aircraft Manufacturer')
plt.grid(axis='x', linestyle='--', alpha=0.7)
plt.tight_layout()

# Add value labels to bars for clarity
for i, v in enumerate(least_accident_makers):
    plt.text(v + 0.2, i, str(v), color='black')

plt.show()


