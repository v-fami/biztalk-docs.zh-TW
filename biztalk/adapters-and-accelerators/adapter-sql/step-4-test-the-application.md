---
title: "步驟 4： 測試應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 488b13fa-7a71-4430-bbf5-dbf47ba55562
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 347c2bcf459d7e9ce7b1fb9efc07579be81d989d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-the-application"></a>步驟 4： 測試應用程式
![步驟 4 之 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：**在此步驟中，您必須測試應用程式所插入在記錄**員工**資料表**ADAPTER_SAMPLES**資料庫。 如果應用程式是否正常運作，協調流程收到變更通知**員工**資料表。 協調流程接著會擷取收到的通知類型。 如果插入作業的通知，協調流程執行**UPDATE_EMPLOYEE**預存程序，並接收回應。 協調流程中擷取的值**Employee_ID**和**名稱**從回應，並將其插入**Purchase_Order**資料表。  
  
## <a name="prerequisites"></a>必要條件  
 開始之前有了這個步驟，您必須確定下列各項：  
  
-   要求訊息來叫用**UPDATE_EMPLOYEE**預存程序將會位於 C:\TestLocation\CreateEmployeeMessage。 要求訊息看起來如下：  
  
    ```  
    <UPDATE_EMPLOYEE xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedProcedures/dbo" />  
    ```  
  
-   在上叫用插入作業的要求訊息**Purchase_Order**資料表將會位於 C:\TestLocation\CreatePOMessage。 要求訊息看起來如下：  
  
    ```  
    <Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Purchase_Order">  
      <Rows>  
        <Purchase_Order xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
          <Employee_ID>10</Employee_ID><Employee_Name>Employee_Name</Employee_Name>  
        </Purchase_Order>  
      </Rows>  
    </Insert>  
    ```  
  
    > [!NOTE]
    >  值**Employee_ID**和**Employee_Name**欄位是預留位置。 實際的值是由協調流程在執行階段插入。  
  
-   您必須先完成[步驟 3： 設定並啟動應用程式](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md)。  
  
### <a name="to-test-the-application"></a>若要測試應用程式  
  
1.  插入資料錄中的**員工**資料表。 您可以從 SQL Server Management Studio 中執行下列陳述式來這麼做。  
  
    ```  
    INSERT INTO [ADAPTER_SAMPLES].[dbo].[Employee] ([Name] ,[Designation] ,[Salary])  
    VALUES('John Smith' ,'Manager' ,500000)  
    ```  
  
2.  請檢查**員工**資料庫中的資料表。 您會注意到新的記錄加**狀態**資料行是"0"。  
  
3.  請重新整理**員工**資料表的記錄。 您會注意到**狀態**新記錄的資料行現在設定為"1"。  
  
4.  請檢查**Purchase_Order**資料表。 您會注意到，將記錄具有相同的員工名稱和指定，如您所提供的 Insert 陳述式中，加入至資料表。  
  
5.  如果您提供您的電子郵件別名，SMTP 連接埠組態中，您也會發生插入作業的回應訊息的電子郵件。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 測試 SampleApplication 應用程式將在資料錄**員工**資料表。  
  
## <a name="next-steps"></a>後續步驟  
 若測試成功，恭喜！ 您已完成[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]教學課程。  
  
 若測試不成功，請仔細地檢查您的工作，以確保您已新增所有必要的物件並正確地設定其屬性。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 設定並啟動應用程式](../../adapters-and-accelerators/adapter-sql/step-3-configure-and-start-the-application.md)   
 [第 5 課： 部署方案](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)