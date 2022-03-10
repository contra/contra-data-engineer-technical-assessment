# Data Engineer Technical Assessment

The purpose of this assignment is to assess your familiarity with the technologies in our data stack. Please read all the instructions carefully. This exercise should take about 1 to 2 hours to complete, but may take longer if you're unfamiliar with [dbt](https://www.getdbt.com/docs/) or need to install additional dependencies locally.

- [Instructions](#instructions)
- [Goal](#goal)
- [Deliverables](#deliverables)
- [Local development environment](#local-development-environment)
- [Helpful resources](#helpful-resources)

## Instructions

1. 2. Set up your local development environment as outlined [here](#local-development-environment).
2. Clone this repository locally.
3. Complete the goal described [below](#goal)
4. Submit all [deliverables](#deliverables)

## Goal

The database instance is a copy of the [Sakila sample database](https://github.com/jOOQ/sakila). The database models the data for a DVD rental store.

[![ERD](https://www.jooq.org/img/sakila.png)](https://www.jooq.org/sakila)

Your goal is to create models to enable an analyst to answer the following question:

> What are the most popular categories of rented films by month?

Add your models to the `models` directory. You can use whatever organization and conventions reflects your understanding of best practices around dbt and data modeling in general. Update `dbt_project.yml` to reflect your changes to the models. You do not need to model all the data in the database, only what's required to answer the question above. However, the models should reflect the fact that additional data may need to be exposed in the future to meet additional data needs.

**Note: When developing locally, make sure to append the `--profiles-dir .` option when running any `dbt` commands so that the provided `profiles.yml` file is used.**

The `dbt run` and `dbt test` commands should execute successfully on a completed project.

Lastly, update `query.sql` with a SQL query that can be executed against the generated model tables to answer the analyst's question.

## Deliverables

Make sure you've committed all your changes, then generate a zip of the local branch:
```sh
git archive HEAD -o assessment.zip
```

## Local development environment

1. If not already installed, install `dbt-postgres` ([instructions](https://docs.getdbt.com/dbt-cli/install/overview))
2. If not already installed, install Docker ([instructions](https://docs.docker.com/get-docker/))
3. Build database image

```sh
docker build --tag contra-assessment .
```

4. Start database

```sh
docker run --name contra-assessment --detach --publish 5438:5432 contra-assessment
```

5. Verify the database is accessible at `postgresql://postgres:workthewayyouwant@localhost:5438/postgres`

## Helpful resources

- Sakila sample database documentation ([link](https://github.com/jOOQ/sakila))
- dbt documentation ([link](https://docs.getdbt.com/docs/introduction))
