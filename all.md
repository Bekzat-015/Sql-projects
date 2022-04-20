7. (insert into [Оценка регулирующего воздействия (ods)].[dbo].[FCproduct]
		([id]
		,[brand]
		,[name]
		,[price])
select d.id,
		d.brand,
		d.name,
		d.price
from [этап(stg)].dbo.Detail d)


select d.id,
		d.brand,
		d.name,
		d.price
		into [Оценка регулирующего воздействия (ods)].[dbo].[FCproduct]
from [этап(stg)].[dbo].[Detail] d

8. 
CREATE TABLE [Оценка регулирующего воздействия (ods)].[dbo].[DmnOrder](
	[id] [int] not null,
	[Brand] [varchar](50) not null,
	[RentPrice] [int] not null
)

insert into [Оценка регулирующего воздействия (ods)].[dbo].[DmnOrder]
		([id],
		[brand],
		[RentPrice])
select id,
		brand,
		RentPrice
from [этап(stg)].[dbo].[Bicycle] 

9.  
CREATE TABLE [Оценка регулирующего воздействия (ods)].[dbo].[ServiceBook](
	[BicycleId] [int] not null,
	[DetailId] [int] not null,
	[Date] [date] not null,
	[Price] [int] not null
)

insert into [Оценка регулирующего воздействия (ods)].[dbo].[ServiceBook]
		([BicycleId],
		[DetailId],
		[Date],
		[Price])
select BicycleId,
		DetailId,
		Date,
		Price
from [этап(stg)].[dbo].[ServiceBook]