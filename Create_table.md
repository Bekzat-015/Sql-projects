1.
USE [этап(stg)]

CREATE TABLE [Detail](
	[Id] [int] NOT NULL,
	[Brand] [varchar](50) NOT NULL,
	[Type] [varchar](50) NOT NULL,
	[Name] [varchar](50) NOT NULL,
	[Price] [int] NOT NULL,
)

2.
USE [этап(stg)]
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
USE [этап(stg)]
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