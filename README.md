# React app to view Nerd Holidays on [Astra DB](https://astra.datastax.com/)

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Astra DB

### Create a new Astra database.

If you do not have an [Astra](https://astra.datastax.com/) account, sign-up for one.  Create a new database.  You can name it whatever you like, but make sure to use "live_coding" as the (default) *keyspace* name.

Pick Google Cloud Platform (GCP) as a provider, and select the region "us-east1" in "Moncks Corner, SC" to get access to the "free" tier.  Your new database should be ready for you in just a few minutes!

Once it is running, you can use Astra CLI

Let's build a quick model to host data on Nerd Holidays.  Open CQL Console (aka cqlsh) on Astra OR use the new [Astra CLI](https://www.datastax.com/blog/introducing-cassandra-astra-cli) to get access to the database console.

First, let's switch over to our "live_coding" keyspace:

```sql
use live_coding;
```

Copy/paste the DDL.

### Table Schema
```sql
CREATE TABLE nerd_holidays (
  year_bucket BIGINT,
  event_date BIGINT,
  name TEXT,
  id UUID,
  PRIMARY KEY ((year_bucket), event_date, id)
) WITH CLUSTERING ORDER BY (event_date ASC, id ASC);
```

Copy/paste the DML.

### Table Data
```sql
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230102,UUID(),'Sci-Fi Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230102,UUID(),'Isaac Asimov''s Birthday');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230115,UUID(),'Apple Computer Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230207,UUID(),'e Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230314,UUID(),'Pi Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230325,UUID(),'Fall of Sauron Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230405,UUID(),'First Contact Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230430,UUID(),'International Tabletop Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230504,UUID(),'Star Wars Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230525,UUID(),'Towel Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230616,UUID(),'Captain Picard Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230628,UUID(),'CAPS LOCK DAY');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230728,UUID(),'SysAdmin Appreciation Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230804,UUID(),'International Beer Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230812,UUID(),'IBM PC Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230919,UUID(),'Talk Like a Pirate Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20230922,UUID(),'Hobbit Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20231002,UUID(),'Ada Lovelace Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20231015,UUID(),'Marty McFly Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20231123,UUID(),'Tardis Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20231123,UUID(),'Fibonacci Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20231130,UUID(),'Computer Security Day');
INSERT INTO nerd_holidays (year_bucket, event_date, id, name)
VALUES (2023,20231221,UUID(),'Rush 2112 Day');
```

## GitPod ##

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/datastaxdevs/workshop-nerd-holidays)

## Environment file

You will need to build a `.env` file in the project's root directory for it to know how to connect to Astra DB.  There is an `.env_sample` file included to help you with this.  Just rename that file to be your new `.env`, edit your values, and you're all set:

```
mv .env_sample .env
```

Edit this file, and define the following variables.  The values can be retrieve from your account on https://astra.datastax.com.

```
REACT_APP_ASTRA_DB_ID=<your-astra-db-id>
REACT_APP_ASTRA_DB_REGION=<your-astra-db-region>
REACT_APP_ASTRA_DB_TOKEN=<your-astra-db-token>
```

## React.js dependencies

Be sure to install the following npm packages:

```
npm install @mui/material @emotion/react @emotion/styled
npm install @mui/x-data-grid
npm install axios
```

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

The page will reload when you make changes.\
