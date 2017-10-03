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
# <a name="getmessages-sample"></a>GetMessages 範例
本主題提供您可以用來從其中一個訊息不可否認性表格，或可讀取格式的其中一個商務營運系統 (LOB) 表格中擷取訊息的範例程式碼。 訊息不可否認性表格包括 [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 封存資料庫中的 MessageStorageIn 和 MessageStorageOut，而 LOB 表格包括 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] DATA 資料庫中的 MessageFromLOB 和 MessageToLOB。  
  
 請使用 `GetMessages` 進行疑難排解或開發。 根據預設，這個程式碼會傳回 base 64 字串。  
  
> [!NOTE]
>  GetMessages.cs 範例程式碼含有兩個程式碼區段，一是會從其中一個 LOB 表格擷取訊息，另一個則是會從其中一個不可否認性表格擷取訊息。 請依照各個用途建立不同的應用程式。  
  
### <a name="to-retrieve-messages-from-an-lob-table"></a>若要從 LOB 表格擷取訊息  
  
1.  將下列範例程式碼加入程式：  
  
     `private static string GetLOBMessage(string sMessageSource, string sMessageID)`  
  
2.  將 `sMessageSource` 參數設定為 MessagesFromLOB 或 MessagesToLOB 表格。  
  
3.  設定`sMessageID`參數的值**MessageID**資料庫中的欄位。  
  
    > [!NOTE]
    >  應用程式會傳回包含所擷取訊息的字串。  
  
### <a name="to-retrieve-messages-from-a-non-repudiation-table"></a>若要從不可否認性表格擷取訊息  
  
1.  將下列範例程式碼加入程式：  
  
     `private static string GetNRMessage(string sMessageSource, string sMessageID)`  
  
2.  將 `sMessageSource` 參數設定為 MessageStorageIn 或 MessageStorageOut 表格。  
  
3.  設定`sMessageID`參數的值**RecordID**資料庫中的欄位。  
  
    > [!NOTE]
    >  應用程式會傳回包含所擷取訊息的字串。  
  
## <a name="demonstrates"></a>示範  
 GetMessages 範例包含下列兩個程式碼區段：  
  
-   一個區段說明如何從其中一個不可否認性表格擷取二進位訊息，並將訊息轉換成為可讀取的 ASCII 格式。  
  
-   另一個區段則說明如何從其中一個 LOB 表格擷取訊息。 由於 LOB 表格中的訊息已經是 ASCII 格式，所以，這是 SQL Select 陳述式。  
  
    > [!IMPORTANT]
    >  為了展示之用，所提供的範例程式碼會使用容易遭受 SQL 資料插入式攻擊的直接 SQL 陳述式。 在實際執行環境中，建議您使用參數化的 SQL 預存程序，而不要使用直接 SQL 陳述式，以預防發生這類弱點。  
  
## <a name="example"></a>範例  
 請在下列程式碼範例中使用上述其中一個程式碼區段，從其中一個不可否認性表格或 LOB 表格擷取訊息。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [傳訊範例](../../adapters-and-accelerators/accelerator-rosettanet/messaging-samples.md)