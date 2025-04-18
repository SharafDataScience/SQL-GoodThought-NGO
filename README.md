# GoodThought NGO Data Insights Project

## Overview

**GoodThought** is a global non-profit organization committed to fostering positive social change through initiatives in education, healthcare, and sustainable development. With operations spanning across underprivileged communities worldwide, GoodThought aims to drive long-term growth and measurable impact.

This project provides a hands-on opportunity to explore GoodThought's PostgreSQL database, allowing for data-driven insights that can enhance the efficiency, transparency, and strategic planning of its operations.

## Database Structure

The database contains detailed records from **2010 to 2023** and is composed of three core tables:

### 1. `assignments`

Represents the various projects initiated by GoodThought.

| Column          | Data Type | Description                              |
|------------------|------------|------------------------------------------|
| assignment_id     | integer    | Primary key                              |
| assignment_name   | varchar    | Name of the assignment                   |
| start_date        | varchar    | Start date of the assignment             |
| end_date          | varchar    | End date of the assignment               |
| budget            | decimal    | Budget allocated to the assignment       |
| region            | varchar    | Geographic region of the assignment      |
| impact_score      | decimal    | Quantitative measure of project impact   |

### 2. `donations`

Captures information on financial contributions from donors.

| Column         | Data Type | Description                                        |
|----------------|------------|----------------------------------------------------|
| donation_id      | integer    | Primary key                                       |
| donor_id         | integer    | Foreign key referencing `donors.donor_id`         |
| amount           | decimal    | Amount donated                                   |
| donation_date    | text       | Date of donation                                 |
| assignment_id    | integer    | Foreign key referencing `assignments.assignment_id` |
| status           | varchar    | Status of the donation (e.g., completed, pending) |
| created_at       | timestamp  | Timestamp when the donation record was created   |

### 3. `donors`

Contains information about the donors funding GoodThought’s initiatives.

| Column      | Data Type | Description                     |
|-------------|------------|---------------------------------|
| donor_id      | integer    | Primary key                    |
| donor_name    | varchar    | Name of the donor              |
| donor_type    | varchar    | Type of donor (individual/org) |

### Entity Relationship

- Each **assignment** can receive **multiple donations**.
- Each **donor** can make **multiple donations**.
- Each **donation** is linked to a single **assignment** and **donor**.

![image](https://github.com/user-attachments/assets/31d59807-c2d0-44ee-b151-1ddecd486f3a) 

## Project Questions

1. **Which are the top five assignments based on the total value of donations, categorized by donor type?**  
   - Output should include: `assignment_name`, `region`, `rounded_total_donation_amount` (rounded to two decimal places), and `donor_type`.  
   - Results should be sorted by total donation amount in descending order.

2. **What is the assignment with the highest impact score in each region, considering only those assignments that received at least one donation?**  
   - Output should include: `assignment_name`, `region`, `impact_score`, and `num_total_donations`.  
   - Return only one assignment per region, sorted by region in ascending order.

## Project Goals

- Analyze donation trends and donor behaviors over time.
- Evaluate assignment effectiveness based on impact scores and funding.
- Identify key donors and regions with significant contributions or results.
- Create visualizations and reports to support strategic decision-making.

## Getting Started

1. Clone the repository.
2. Open the `notebook.ipynb` file for exploratory data analysis.
3. Ensure you have access to the PostgreSQL database (or a provided export).
4. Install required Python libraries (if needed):
   ```bash
   pip install pandas matplotlib seaborn sqlalchemy psycopg2
