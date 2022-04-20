1.
USE [����(stg)]

CREATE TABLE [Detail](
	[Id] [int] NOT NULL,
	[Brand] [varchar](50) NOT NULL,
	[Type] [varchar](50) NOT NULL,
	[Name] [varchar](50) NOT NULL,
	[Price] [int] NOT NULL,
)

2.
USE [����(stg)]
GO

/****** Object:  Table [dbo].[Bicycle]    Script Date: 14.04.2022 8:27:32 ******/
SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [dbo].[Bicycle](
	[Id] [int] NOT NULL,
	[Brand] [varchar](50) NOT NULL,
	[RentPrice] [int] NOT NULL,
	)
3.
USE [����(stg)]
GO

/****** Object:  Table [dbo].[ServiceBook]    Script Date: 14.04.2022 8:35:51 ******/
SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [ServiceBook](
	[BicycleId] [int] NOT NULL,
	[DetailId] [int] NOT NULL,
	[StaffId] [int] NOT NULL,
	[Date] [date] NOT NULL,
	[Price] [int] NOT NULL
	) 

4.
insert into [����(stg)].dbo.Detail (
	[Id],
	[Brand],
	[Type],
	[Name],
	[Price]
)
select [Id],
	[Brand],
	[Type],
	[Name],
	[Price] from [job].[dbo].[Detail] 
where [Price] = (select max(Price) from [job].dbo.[Detail]) 

5.
insert into [����(stg)].dbo.ServiceBook(
	[BicycleId],
	[DetailId],
	[StaffId],
	[Date],
	[Price]
	)
select [BicycleId],
	[DetailId],
	[StaffId],
	[Date],
	[Price] from [job].[dbo].[ServiceBook] 
where [Price] = (select max(Price) from [job].dbo.[ServiceBook])

6. insert into [����(stg)].dbo.[Bicycle](
	[Id],
	[Brand],
	[RentPrice]
	)
select [Id],
	[Brand],
	[RentPrice] from [job].[dbo].[Bicycle] 
where [RentPrice] = (select max([RentPrice]) from [job].dbo.[Bicycle])

7. (insert into [������ ������������� ����������� (ods)].[dbo].[FCproduct]
		([id]
		,[brand]
		,[name]
		,[price])
select d.id,
		d.brand,
		d.name,
		d.price
from [����(stg)].dbo.Detail d)


select d.id,
		d.brand,
		d.name,
		d.price
		into [������ ������������� ����������� (ods)].[dbo].[FCproduct]
from [����(stg)].[dbo].[Detail] d

8. 
CREATE TABLE [������ ������������� ����������� (ods)].[dbo].[DmnOrder](
	[id] [int] not null,
	[Brand] [varchar](50) not null,
	[RentPrice] [int] not null
)

insert into [������ ������������� ����������� (ods)].[dbo].[DmnOrder]
		([id],
		[brand],
		[RentPrice])
select id,
		brand,
		RentPrice
from [����(stg)].[dbo].[Bicycle] 

9.  
CREATE TABLE [������ ������������� ����������� (ods)].[dbo].[ServiceBook](
	[BicycleId] [int] not null,
	[DetailId] [int] not null,
	[Date] [date] not null,
	[Price] [int] not null
)

insert into [������ ������������� ����������� (ods)].[dbo].[ServiceBook]
		([BicycleId],
		[DetailId],
		[Date],
		[Price])
select BicycleId,
		DetailId,
		Date,
		Price
from [����(stg)].[dbo].[ServiceBook]
