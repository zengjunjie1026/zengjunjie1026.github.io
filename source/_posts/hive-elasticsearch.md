---
title: hive elasticsearch
date: 2023-08-20 09:09:15
tags: server
---


## 需要同步的elastic表
```hive
add jar hdfs:///elasticsearch-jars/elasticsearch-hadoop-hive-8.1.1.jar;
-- create database ods_beike;
CREATE EXTERNAL TABLE ods_beike.ershoufang_detail_from_es(

house_url string comment 'house url',
house_id string comment 'house id',
title string comment '标题',
unit string comment '',
main_info string comment '厅房',
type_main string comment 'direction',
type_sub string comment  '',
district_detail string comment  '',
districr_url  string comment  '小区url',
district_detail_url string comment  '',
communityname string comment  '小区信息',
communityurl string  comment '小区url',
district string comment '区或者县',
area string comment '房子面积',
year string comment '建成年份',
fetch_time timestamp,
fundamental_values
    struct<
  house_con : string,
       house_floor:string,
     house_area:string,
        house_struct:string,
       house_contruct_type:string,
       house_direction:string,
       house_construction:string,
        house_detraction:string,
       elevtor_percent:string,
      warn_type:string,
       has_elevtor:string,
       gas_price:string,
        bighouse_type:string,
    userful_area:string,
        water_type:string,
        power_type:string,
        rent_area:string

    >,

sells_values  struct<
up_time: string ,--comment '挂牌时间',
sell_type: string, --comment  --"交易权属",
 last_sell: string, --comment --"上次交易",
 house_type :string, --comment -- "房屋用途",
house_age :string, --comment  --"房屋年限": ,
 property_type: string ,--comment  ,--"产权所属",
 mostage_type: string ,--comment  ,--"抵押信息",
 house_paper: string ,--comment ,-- "房本备件" ,
 house_validation_code :string ,--comment  "房源核验码",
house_validation_code2: string ,-- comment  '房源核验统一编码' ,
house_validation_code3 :string ,--comment  '房管局核验码' ,
 house_code: string, --comment  '房源编码',
 code4: string,-- comment , --"房源核验编码",
code5: string --comment --comment '房协编码'
>
)
STORED BY 'org.elasticsearch.hadoop.hive.EsStorageHandler'
TBLPROPERTIES(
    'es.resource' = 'beike_ershoufang_details_english/doc',
    'es.nodes' = 'http://10.147.20.10',
    'es.port'='9200',
    'es.index.auto.create'='false',
    'es.read.metadata'='true'
);

## 目的表
add jar hdfs:///elasticsearch-jars/elasticsearch-hadoop-hive-8.1.1.jar;
-- create database ods_beike;
CREATE EXTERNAL TABLE ods_beike.ershoufang_detail_from_es2(

house_url string comment 'house url',
house_id string comment 'house id',
title string comment '标题',
unit string comment '',
main_info string comment '厅房',
type_main string comment 'direction',
type_sub string comment  '',
district_detail string comment  '',
districr_url  string comment  '小区url',
district_detail_url string comment  '',
communityname string comment  '小区信息',
communityurl string  comment '小区url',
district string comment '区或者县',
area string comment '房子面积',
year string comment '建成年份',
fetch_time timestamp,
fundamental_values
    struct<
  house_con : string,
       house_floor:string,
     house_area:string,
        house_struct:string,
       house_contruct_type:string,
       house_direction:string,
       house_construction:string,
        house_detraction:string,
       elevtor_percent:string,
      warn_type:string,
       has_elevtor:string,
       gas_price:string,
        bighouse_type:string,
    userful_area:string,
        water_type:string,
        power_type:string,
        rent_area:string

    >,

sells_values  struct<
up_time: string ,--comment '挂牌时间',
sell_type: string, --comment  --"交易权属",
 last_sell: string, --comment --"上次交易",
 house_type :string, --comment -- "房屋用途",
house_age :string, --comment  --"房屋年限": ,
 property_type: string ,--comment  ,--"产权所属",
 mostage_type: string ,--comment  ,--"抵押信息",
 house_paper: string ,--comment ,-- "房本备件" ,
 house_validation_code :string ,--comment  "房源核验码",
house_validation_code2: string ,-- comment  '房源核验统一编码' ,
house_validation_code3 :string ,--comment  '房管局核验码' ,
 house_code: string, --comment  '房源编码',
 code4: string,-- comment , --"房源核验编码",
code5: string --comment --comment '房协编码'
>
)
STORED BY 'org.elasticsearch.hadoop.hive.EsStorageHandler'
TBLPROPERTIES(
    'es.resource' = 'beike_ershoufang_details_english/doc',
    'es.nodes' = 'http://10.147.20.96',
    'es.port'='9200',
    'es.index.auto.create'='false',
    'es.read.metadata'='true'
);

## 同步

select count(*) from  ods_beike.ershoufang_detail_from_es2;
desc ods_beike.ershoufang_detail_from_es2;

insert into table ods_beike.ershoufang_detail_from_es2
select * from ods_beike.ershoufang_detail_from_es;

select count(*) from  ods_beike.ershoufang_detail_from_es2;


```