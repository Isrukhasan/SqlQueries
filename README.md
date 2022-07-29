# SqlQueries
Get Asp net users with role 

USE [TestDatabaseTest]
GO
/****** Object:  StoredProcedure [dbo].[GetRoleNameByUserId]    Script Date: 7/29/2022 11:12:14 AM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

--GetRoleNameByUserId '1c583572-f8eb-45e2-ab96-89d304ad4700'
-- =============================================
-- Author:		Isruk
-- Create date: 2022-01-11
-- Description:	<Description,,>
-- =============================================
ALTER PROCEDURE [dbo].[GetRoleNameByUserId]
@userId nvarchar(500)
AS
BEGIN
	
	
SELECT U.Email ,R.Name,U.Id
FROM AspNetUsers U
INNER JOIN AspNetUserRoles UR
    ON U.Id=UR.UserId
INNER JOIN AspNetRoles R
    ON UR.RoleId=R.Id

where @userId=U.Id

END
