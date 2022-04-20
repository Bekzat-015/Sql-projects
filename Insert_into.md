4.
insert into [этап(stg)].dbo.Detail (
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
insert into [этап(stg)].dbo.ServiceBook(
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

6. insert into [этап(stg)].dbo.[Bicycle](
	[Id],
	[Brand],
	[RentPrice]
	)
select [Id],
	[Brand],
	[RentPrice] from [job].[dbo].[Bicycle] 
where [RentPrice] = (select max([RentPrice]) from [job].dbo.[Bicycle])
