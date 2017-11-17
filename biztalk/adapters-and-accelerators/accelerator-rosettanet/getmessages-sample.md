---
title: "GetMessages 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29e575fa-d68b-4975-84b8-da4f17bd2db3
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2ebc4ce5b87a0b698f0295fdf29c8f7138efed7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="getmessages-sample"></a><span data-ttu-id="ee12e-102">GetMessages 範例</span><span class="sxs-lookup"><span data-stu-id="ee12e-102">GetMessages Sample</span></span>
<span data-ttu-id="ee12e-103">本主題提供您可以用來從其中一個訊息不可否認性表格，或可讀取格式的其中一個商務營運系統 (LOB) 表格中擷取訊息的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="ee12e-103">This topic provides sample code that you can use to retrieve messages from one of the message non-repudiation tables or one of the line-of-business (LOB) tables in a readable form.</span></span> <span data-ttu-id="ee12e-104">訊息不可否認性表格包括 [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 封存資料庫中的 MessageStorageIn 和 MessageStorageOut，而 LOB 表格包括 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] DATA 資料庫中的 MessageFromLOB 和 MessageToLOB。</span><span class="sxs-lookup"><span data-stu-id="ee12e-104">The message non-repudiation tables include MessageStorageIn and MessageStorageOut in the [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]Archive database; the LOB tables include MessageFromLOB and MessageToLOB in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA database.</span></span>  
  
 <span data-ttu-id="ee12e-105">請使用 `GetMessages` 進行疑難排解或開發。</span><span class="sxs-lookup"><span data-stu-id="ee12e-105">Use `GetMessages` for either troubleshooting or development.</span></span> <span data-ttu-id="ee12e-106">根據預設，這個程式碼會傳回 base 64 字串。</span><span class="sxs-lookup"><span data-stu-id="ee12e-106">By default, the code returns a base 64 string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee12e-107">GetMessages.cs 範例程式碼含有兩個程式碼區段，一是會從其中一個 LOB 表格擷取訊息，另一個則是會從其中一個不可否認性表格擷取訊息。</span><span class="sxs-lookup"><span data-stu-id="ee12e-107">The GetMessages.cs sample code contains two sections of code—one for retrieving messages from one of the LOB tables, and one for retrieving messages from one of the non-repudiation tables.</span></span> <span data-ttu-id="ee12e-108">請依照各個用途建立不同的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ee12e-108">Create separate applications for each purpose.</span></span>  
  
### <a name="to-retrieve-messages-from-an-lob-table"></a><span data-ttu-id="ee12e-109">若要從 LOB 表格擷取訊息</span><span class="sxs-lookup"><span data-stu-id="ee12e-109">To retrieve messages from an LOB table</span></span>  
  
1.  <span data-ttu-id="ee12e-110">將下列範例程式碼加入程式：</span><span class="sxs-lookup"><span data-stu-id="ee12e-110">Add the following sample code to your program:</span></span>  
  
     `private static string GetLOBMessage(string sMessageSource, string sMessageID)`  
  
2.  <span data-ttu-id="ee12e-111">將 `sMessageSource` 參數設定為 MessagesFromLOB 或 MessagesToLOB 表格。</span><span class="sxs-lookup"><span data-stu-id="ee12e-111">Set the `sMessageSource` parameter to either the MessagesFromLOB or MessagesToLOB table.</span></span>  
  
3.  <span data-ttu-id="ee12e-112">設定`sMessageID`參數的值**MessageID**資料庫中的欄位。</span><span class="sxs-lookup"><span data-stu-id="ee12e-112">Set the `sMessageID` parameter to the value of the **MessageID** field in the database.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ee12e-113">應用程式會傳回包含所擷取訊息的字串。</span><span class="sxs-lookup"><span data-stu-id="ee12e-113">The application returns a string that contains the retrieved message.</span></span>  
  
### <a name="to-retrieve-messages-from-a-non-repudiation-table"></a><span data-ttu-id="ee12e-114">若要從不可否認性表格擷取訊息</span><span class="sxs-lookup"><span data-stu-id="ee12e-114">To retrieve messages from a non-repudiation table</span></span>  
  
1.  <span data-ttu-id="ee12e-115">將下列範例程式碼加入程式：</span><span class="sxs-lookup"><span data-stu-id="ee12e-115">Add the following sample code to your program:</span></span>  
  
     `private static string GetNRMessage(string sMessageSource, string sMessageID)`  
  
2.  <span data-ttu-id="ee12e-116">將 `sMessageSource` 參數設定為 MessageStorageIn 或 MessageStorageOut 表格。</span><span class="sxs-lookup"><span data-stu-id="ee12e-116">Set the `sMessageSource` parameter to either the MessageStorageIn or MessageStorageOut table.</span></span>  
  
3.  <span data-ttu-id="ee12e-117">設定`sMessageID`參數的值**RecordID**資料庫中的欄位。</span><span class="sxs-lookup"><span data-stu-id="ee12e-117">Set the `sMessageID` parameter to the value of the **RecordID** field in the database.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ee12e-118">應用程式會傳回包含所擷取訊息的字串。</span><span class="sxs-lookup"><span data-stu-id="ee12e-118">The application returns a string that contains the retrieved message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="ee12e-119">示範</span><span class="sxs-lookup"><span data-stu-id="ee12e-119">Demonstrates</span></span>  
 <span data-ttu-id="ee12e-120">GetMessages 範例包含下列兩個程式碼區段：</span><span class="sxs-lookup"><span data-stu-id="ee12e-120">The GetMessages sample includes the following two sections of code:</span></span>  
  
-   <span data-ttu-id="ee12e-121">一個區段說明如何從其中一個不可否認性表格擷取二進位訊息，並將訊息轉換成為可讀取的 ASCII 格式。</span><span class="sxs-lookup"><span data-stu-id="ee12e-121">One section shows you how to retrieve a binary message from one of the non-repudiation tables, and convert it into readable ASCII form.</span></span>  
  
-   <span data-ttu-id="ee12e-122">另一個區段則說明如何從其中一個 LOB 表格擷取訊息。</span><span class="sxs-lookup"><span data-stu-id="ee12e-122">The other section shows you how to retrieve a message from one of the LOB tables.</span></span> <span data-ttu-id="ee12e-123">由於 LOB 表格中的訊息已經是 ASCII 格式，所以，這是 SQL Select 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ee12e-123">Because a message in an LOB table is already in ASCII form, this is a SQL select statement.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ee12e-124">為了展示之用，所提供的範例程式碼會使用容易遭受 SQL 資料插入式攻擊的直接 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ee12e-124">For demonstration purposes, the sample code provided uses a direct SQL statement that is prone to SQL injection vulnerabilities.</span></span> <span data-ttu-id="ee12e-125">在實際執行環境中，建議您使用參數化的 SQL 預存程序，而不要使用直接 SQL 陳述式，以預防發生這類弱點。</span><span class="sxs-lookup"><span data-stu-id="ee12e-125">In a production environment, it is recommended that you use parameterized SQL stored procedures, instead of the direct SQL statement, to prevent such vulnerabilities.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee12e-126">範例</span><span class="sxs-lookup"><span data-stu-id="ee12e-126">Example</span></span>  
 <span data-ttu-id="ee12e-127">請在下列程式碼範例中使用上述其中一個程式碼區段，從其中一個不可否認性表格或 LOB 表格擷取訊息。</span><span class="sxs-lookup"><span data-stu-id="ee12e-127">Use one of the two sections in the following code example for retrieving messages from one of the non-repudiation tables or one of the LOB tables.</span></span>  
  
```  
using System;  
using System.Text;  
using System.Data.SqlClient;   
using Microsoft.Solutions.BTARN.Shared;  
  
namespace Microsoft.Solutions.BTARN.Admin  
{  
  
      /// <summary>  
      /// Summary description for GetMessages.  
      /// </summary>  
      class GetMessages  
      {  
            /// <summary>  
            /// The main entry point for the application.  
            /// </summary>  
            [STAThread]  
            static void Main(string[] args)  
            {  
                  Console.WriteLine(GetLOBMessage("MessagesFromLOB", "bce5b580daf543a990a4f37331f31e42"));  
                  Console.WriteLine(GetLOBMessage("MessagesToLOB", "bce5b580daf543a990a4f37331f31e42"));  
                  Console.WriteLine(GetNRMessage("MessageStorageIn", "dc06e9cfecd746a889dd6ea7beb3ba21"));  
                  Console.WriteLine(GetNRMessage("MessageStorageOut", "dc06e9cfecd746a889dd6ea7beb3ba21"));  
            }  
  
            /// <summary>  
            /// Retrieve a message from the LOB tables in the BTARNDATA database  
            /// </summary>  
            /// <param name="sMessageSource">Can be either MessagesFromLOB or MessagesToLOB</param>  
            /// <param name="sMessageID">The value of the MessageID field in the database</param>  
            /// <returns>Returns a string that contains the retrieved message</returns>        
            private static string GetLOBMessage(string sMessageSource, string sMessageID)  
            {  
                  SqlDataReader localReader = null;  
                  SqlConnection sqlConnection = null;  
                  SqlCommand sqlCommand = null;  
                  string sReturnedMessage="";              
                  string sQuery;  
  
                  sqlConnection = new SqlConnection(RuntimeGlobal.DataDbConnectionString);  
                  sQuery = "SELECT ServiceContent from " + sMessageSource + " WHERE MessageID=N'" + sMessageID +"'";  
  
                  sqlCommand = new SqlCommand(sQuery, sqlConnection);  
                  sqlConnection.Open();  
  
                  localReader = sqlCommand.ExecuteReader();  
  
                  if (localReader.Read())  
                        sReturnedMessage=localReader.GetString(0);  
  
                  localReader.Close();  
                  sqlConnection.Close();        
                  return sReturnedMessage;              
            }  
  
            /// <summary>  
            /// Retrieve a message from the non-repudiation tables in the BTARNArchive database  
            /// </summary>  
            /// <param name="sMessageSource">Can be either MessageStorageIn or MessageStorageOut</param>  
            /// <param name="sMessageID">The value of the RecordID field in the database</param>  
            /// <returns>Returns a string that contains the retrieved message</returns>  
            private static string GetNRMessage(string sMessageSource, string sMessageID)  
            {  
                  SqlDataReader localReader = null;  
                  SqlConnection sqlConnection = null;  
                  SqlCommand sqlCommand = null;  
                  string sReturnedMessage="";              
                  string sQuery;  
  
                  sqlConnection = new SqlConnection(RuntimeGlobal.ArchiveDbConnectionString);  
                  sQuery = "SELECT Content from " + sMessageSource + " WHERE RecordID=N'" + sMessageID +"'";  
  
                  sqlCommand = new SqlCommand(sQuery, sqlConnection);  
                  sqlConnection.Open();  
  
                  localReader = sqlCommand.ExecuteReader();  
  
                  if (localReader.Read())  
                  {  
                        //Determine the size of the field in bytes and create a new byte array  
                        byte[] bData= new byte[localReader.GetBytes(0, 0, null, 0, 0)];  
  
                        //Read the value of the field into bData  
                        localReader.GetBytes(0, 0, bData, 0, bData.Length);  
  
                        //Convert the byte array into a string  
                        sReturnedMessage=Encoding.ASCII.GetString(bData);  
                  }  
  
                  localReader.Close();  
                  sqlConnection.Close();        
                  return sReturnedMessage;              
            }  
      }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee12e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee12e-128">See Also</span></span>  
 [<span data-ttu-id="ee12e-129">傳訊範例</span><span class="sxs-lookup"><span data-stu-id="ee12e-129">Messaging Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/messaging-samples.md)