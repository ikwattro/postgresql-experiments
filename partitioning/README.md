# Partitioning

## Partitioning by list

```
docker exec -it postgres sh
psql -U postgres
```

```
CREATE TABLE sales_region (id int, amount int, country text, region text)
PARTITION BY LIST (region)
;
```

```
CREATE TABLE sales_region_apac PARTITION OF sales_region FOR VALUES IN ('APAC');
CREATE TABLE sales_region_europe PARTITION OF sales_region FOR VALUES IN ('EUROPE');
```

```
INSERT INTO sales_region (id, amount, country, region)
VALUES (1, 1000, 'Australia', 'APAC')
;
```

```
INSERT INTO sales_region_europe (id, amount, country, region)
VALUES (2, 1100, 'France', 'EUROPE')
;
```

```
INSERT INTO sales_region_europe (id, amount, country, region)
VALUES (3, 1150, 'Germany', 'EUROPE')
;
```