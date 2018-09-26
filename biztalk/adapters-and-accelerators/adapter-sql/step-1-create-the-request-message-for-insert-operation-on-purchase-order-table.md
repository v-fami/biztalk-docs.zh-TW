---
title: 步驟 1： 建立要求訊息 Purchase_Order 資料表的 Insert 作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fde018d8-9d9a-42ea-8ee9-e3632450b9d7
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71021bb0a9bbb71f17f0899e625ac184f9087429
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25966004"
---
# <a name="step-1-create-the-request-message-for-insert-operation-on-purchaseorder-table"></a>步驟 1： 建立要求訊息 Purchase_Order 資料表的 Insert 作業
![步驟 4 之 1](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，您必須將 C# 類別庫專案加入至方案。 此文件庫上建立記憶體中要求訊息的 Insert 作業**Purchase_Order**資料表。 在稍後步驟中，協調流程會將此訊息傳送到 SQL Server 資料表中插入記錄。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成中的步驟[第 3 課： 執行預存程序來選取新加入的員工](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)。  
  
### <a name="to-create-a-request-message-for-insert-operation"></a>若要建立用於插入作業的要求訊息  
  
1.  將 Visual C# 類別庫專案加入至方案。 如需專案的名稱，輸入`UpdatePOMessageCreator`。  
  
2.  重新命名**Class1.cs**至**UpdatePOMessageCreator.cs**。  
  
3.  將下列程式碼複製到.cs 檔案中：  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Xml;  
    using System.IO;  
  
    namespace UpdatePOMessageCreator  
    {  
        public class UpdatePOMessageCreator  
        {  
            private static XmlDocument Message;  
            private static string XmlFileLocation;  
            private static string ResponseDoc;  
  
            public static XmlDocument XMLMessageCreator()  
            {  
                XmlFileLocation = "C:\\TestLocation\\CreatePOMessage";  
                try  
                {  
                    ResponseDoc = (Directory.GetFiles(XmlFileLocation, "*.xml", SearchOption.TopDirectoryOnly))[0];  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine("Trying to get XML from: " + XmlFileLocation);  
                    Console.WriteLine("EXCEPTION: " + ex.ToString());  
                    throw ex;  
                }  
  
                //Create Message From XML  
                Message = new XmlDocument();  
  
                Message.PreserveWhitespace = true;  
  
                Message.Load(ResponseDoc);  
  
                return Message;  
            }  
        }  
    }  
  
    ```  
  
     此程式碼片段必須插入作業的要求訊息上**Purchase_Order**守在 C:\TestLocation\CreatePOMessage 的資料表。 程式碼會使用要求訊息，在執行階段建立類似的要求訊息。  
  
4.  將強式名稱金鑰檔加入專案。 如需建立強式名稱金鑰檔的指示，請參閱[來建立使用 SQL 配接器的 SQL 應用程式的必要條件](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md)。  
  
    1.  在 [方案總管] 中，以滑鼠右鍵按一下**UpdatePOMessageCreator**專案，然後按一下**屬性**。  
  
    2.  在**屬性**視窗中，按一下 **簽署**。  
  
    3.  在**簽署**索引標籤上，選取**簽署組件**核取方塊。  
  
    4.  從**選擇強式名稱金鑰檔**清單中，按一下**\<瀏覽\>**。  
  
    5.  導覽至您用來建立強式名稱金鑰檔案的資料夾，然後按一下**開啟**。  
  
    6.  按一下**儲存**上**標準**功能表列。 關閉**屬性**視窗。  
  
5.  建置專案。 以滑鼠右鍵按一下專案，然後按一下**建置**。  
  
6.  這個專案的參考加入至方案中的 BizTalk 專案。  
  
    1.  在 方案總管 中，展開 BizTalk 專案，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。  
  
    2.  在**加入參考**對話方塊中，按一下 [**專案**] 索引標籤。  
  
    3.  從 專案名稱的清單，選取  **UpdatePOMessageCreator**，按一下**新增**，然後按一下**確定**。  
  
7.  建置專案時，會建立組件 DLL 專案的 \bin\Debug 資料夾下。 您必須加入這個 DLL 到全域組件快取 (GAC) 中。  
  
    1.  啟動 Visual Studio 命令提示字元。  
  
    2.  從命令提示字元中，瀏覽至的 \bin\Debug\ 資料夾**UpdatePOMessageCreator**專案。  
  
    3.  在命令提示字元處執行下列命令：  
  
        ```  
        gacutil /i UpdatePOMessageCreator.dll  
        ```  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您可以加入 UpdatePOMessageCreator 類別庫專案會建立在執行階段的要求訊息。 您在 BizTalk 專案中加入此專案的參考，也加入至 GAC 的組件 DLL。  
  
## <a name="next-steps"></a>後續步驟  
 您在對應的插入作業的要求訊息的 UPDATE_EMPLOYEE 預存程序的回應訊息**Purchaser_Order**資料表。  
  
## <a name="see-also"></a>請參閱  
 [步驟 2： 將 UPDATE_EMPLOYEE 回應訊息對應至插入作業要求訊息](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md)   
 [第 4 課：在訂單資料表上執行插入作業](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)