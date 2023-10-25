---
marp: true
theme: gaia
---

<style>
blockquote {
  background: #ffedcc;
  border-left: 20px solid #d1bf9d;
  margin: 1.5em 10px;
  padding: 0.5em 10px;
}
</style>

<!-- _class: lead -->

![bg right w:500px](assets/equal-experts-logo-white-blue-background.png)

# TDD for Data Engineering

Guillaume (**G**) Belrose

--- 
<!-- header: ![image w:120px](assets/equal-experts-logo-white-blue-background.png) -->

![bg w:75%](assets/hands-up.jpg) 

--- 

![bg h:75%](assets/darth-vader-meme.jpg) 

<!-- _footer: Make your own: https://imgflip.com/memegenerator/19005569/Darth-Vader -->

---

<!-- paginate: true -->
<!-- footer: TDD for Data Engineering -->

# Agenda

- Some context on Data Engineering
- EL**T** Data Pipelines
- Data Pipelines with TDD
- Experiences from production

---

# What: Data Pipelines

![bg w:95%](assets/data-engineering.png) 

---

# How: ~~Software~~ Data Engineering principles

- **TDD** / unit testing
- Automation
- CI/CD
- Telemetry
- Operability
- Iterative and incremental approaches

---

# Test Driven Development

* Write the test first :red_circle:
* Write the code to pass the test :green_circle:
* Keep on refactoring the logic (cleaner, more expressive)
* Dave Farley's [TDD Is The Best Design Technique](https://www.youtube.com/watch?v=ln4WnxX-wrw)

---

# EL**T** Data Pipelines

![bg h:60%](assets/elt-stack.png) 

---

# dbt (Data Build Tool)

- Open-source CLI tool to build, test and maintain data pipelines
- Transform data in the warehouse via **SELECT** statements
- Suitable for anyone with **SQL** skills
- Easy to learn [fundamentals](https://courses.getdbt.com/courses/fundamentals) 
- Built-in support **data quality checks**

---

![bg right w:80%](assets/dbt-ref.png)

# Some concepts

- Jinja2 SQL templating engine
- **Models** and **references**
- Macros

---

# A Star Wars Data Pipeline

![bg h:60%](assets/star-wars-data-pipeline.png) 

<!-- _footer: TDD for Data Engineering | Star Wars dataset: https://www.kaggle.com/datasets/jsphyg/star-wars -->

---

# dbt-unit-testing

- https://github.com/EqualExperts/dbt-unit-testing
- Extend dbt test with unit testing capability
- `Adopt` on the Thoughtworks [radar](https://www.thoughtworks.com/radar/tools/dbt)

---

# A Star Wars Data Pipeline with TDD 

![bg w:80%](assets/star-wars-data-pipeline-with-tdd.png) 

---
# Experiences from production

![bg w:95%](assets/tales-from-production.png) 

---
# Data Ingestion Pipeline

* Suppliers file formats (deeply nested JSON, fixed length format)
* Parsing logic in SQL (text manipulation, regex, JSON unmarshalling in Snowflake)
* Mock **incoming data** to validate logic

---
# Data Export Pipeline

* Data contract agreed with 3rd party consumer
* Format mapping (dates, flags, phone numbers)
* Non trivial business logic to **produce** the data
* Mock the **in warehouse data** to validate logic

---
# Data Compliance Pipeline

* Respect of GDPR rules
* Data to be erased or anonymised
* Complicated business logic to identify suitable records (e.g. claims)
* Complicated logic to anonymise data (back to the raw layer)

---

# Findings

* For anything non trivial !!!
* TDD **guides** design (CTE vs subquery, testable features)
* Tests make you comfortable to **refactor** code
* Much faster **feedback loop** (compared with integration tests)
* **Documentation** as a side effect

---

# Findings: production issues
- Write a test case to replicate the problem
- Implement the fix 

---

# What if I don't use DBT?

- ELT pipelines: [SQLMesh](https://sqlmesh.com/), Google [dataform](https://cloud.google.com/dataform?hl=en)
- TDD is a **practice**, try to apply it with your stack
- Supported in many languages (Python, Scala)
- Supported in many frameworks (Spark)

---

# The data quality arsenal

> Organizations need good quality data for decision-making and insights
* TDD is one part of the puzzle :jigsaw: 
* Integration tests
* Data Quality Checks
* Alerting & Monitoring

--- 

<!-- _class: lead -->

# Thank you!
