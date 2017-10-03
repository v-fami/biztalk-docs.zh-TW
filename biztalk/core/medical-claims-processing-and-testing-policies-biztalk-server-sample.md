---
title: "醫療理賠處理和測試原則 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, business rules
- business rules, examples
ms.assetid: c0bdf7b7-3e55-4560-a5a8-00c5b661d14d
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33c8921e037b9f9628c0e0ee97a915f62ab634ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="medical-claims-processing-and-testing-policies-biztalk-server-sample"></a>醫療理賠處理和測試原則 （BizTalk Server 範例）
「醫療理賠處理和測試原則」範例示範如何建立一組規則集，其中多個規則會檢查衍生自資料庫資料表的事實和輸入文件，並使用 .NET 架構物件來記錄理賠處理的結果。  
  
 這個範例會示範端對端執行理賠處理的實例，透過使用「商務規則引擎」的簡單 .NET 架構應用程式，對輸入的理賠申請執行醫療理賠規則集，判斷理賠申請的 STATUS 及其 REASON。  
  
> [!NOTE]
>  這個範例也會示範如何使用偵錯追蹤檔案，追蹤「商務規則引擎」的執行狀況。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 這個範例會將下列一連串規則套用至提交的理賠申請：  
  
1.  如果理賠申請的總金額超過原則允許的上限，則拒絕理賠申請。  
  
2.  如果客戶住院天數超過原則允許的上限，則拒絕理賠申請。  
  
3.  如果理賠申請上的日期是在未來，則拒絕理賠申請。  
  
4.  如果原則無效則拒絕理賠申請。  
  
5.  如果原則已過期，則傳送線索給銷售部門並附上原則識別碼和客戶名稱。  
  
6.  否則核准理賠申請。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*範例路徑*> \Business Rules\Medical 理賠處理和測試 Policies\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|Cleanup.bat|用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。 移除傳送埠和接收埠。 視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|Create_PolicyValidity_Table.sql|將新資料表 PolicyValidity 加入 Northwind 範例資料庫的 SQL 指令碼。|  
|Setup.bat|用來建置和初始化此範例。|  
|在 \Claims 資料夾中：<br /><br /> AssemblyInfo.cs、Claims.csproj、Claims.sln、Claims.cs|專案、 解決方案、 來源和相關的檔案，這個記錄理賠處理，結果的範例的一部分呼叫**然後**規則的一部分。|  
|在 \FactRetrieverForClaimsProcessing 資料夾中：<br /><br /> AssemblyInfo.cs、FactRetrieverForClaimsProcessing.cs、FactRetrieverForClaimsProcessing.csproj、FactRetrieverForClaimsProcessing.sln|這個範例所屬的專案、解決方案、來源和相關檔案，其提供長期事實擷取器 (會從這個範例所建立的 PolicyValidity 資料表擷取資訊)。|  
|在 \RulesForMedicalClaims 資料夾中：<br /><br /> App.ico、AssemblyInfo.cs、RulesForMedicalClaims.cs、RulesForMedicalClaims.csproj、RulesForMedicalClaims.sln|專案、 解決方案、 來源和相關的檔案的一部分，其構成此範例 (RulesForMedicalClaims.exe)，以及哪些主要可執行檔以程式設計方式定義及儲存規則集，建構範例事實，然後執行規則集使用**PolicyTester**物件。|  
|在 \RulesForMedicalClaims 資料夾中：<br /><br /> MedicalClaims.xsd|結構描述檔案，定義提交至此範例之範例醫療理賠申請的結構。|  
|在 \RulesForMedicalClaims 資料夾中：<br /><br /> sampleClaim.xml|範例輸入檔，與 MedicalClaims.xsd 檔中定義的結構描述相符。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
  
#### <a name="to-build-and-initialize-the-medical-claims-processing-and-testing-policies-sample"></a>若要建置及初始化醫療理賠處理和測試原則範例  
  
1.  確定您的電腦上已安裝 Northwind 資料庫。  
  
    > [!IMPORTANT]
    >  您必須已安裝名為 Northwind 的資料庫，才能執行此範例。 [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]和[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]並未隨附 Northwind 範例資料庫。 如果要建立 Northwind 資料庫，請從安裝檔案下載[http://go.microsoft.com/fwlink/?LinkId=196020](http://go.microsoft.com/fwlink/?LinkId=196020)，並遵循指示。  
  
2.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*> \Business Rules\Medical 理賠處理和測試 Policies\  
  
3.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   為這個範例編譯及部署 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案，包括 Claims.dll、FactRetrieverForClaimsProcessing.dll 和 RulesForMedicalClaims.dll。  
  
    > [!NOTE]
    >  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。  
  
    > [!NOTE]
    >  若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 使用此金鑰組簽署所產生的組件。  
  
    -   使用 SQL Query Analyzer 執行所提供的 SQL 指令碼 Create_PolicyValidity_Table.sql。 此指令碼會使用 Northwind 範例資料庫中的兩個範例資料列來建立資料表 PolicyValidity。 這個資料表有兩個資料行： ID 和 PolicyStatus。  
  
    -   建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送和接收埠。  
  
    -   啟用接收位置並啟動傳送埠。  
  
    -   登錄和啟動協調流程。  
  
    > [!NOTE]
    >  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
## <a name="running-this-sample"></a>執行此範例  
  
#### <a name="to-run-the-medical-claims-processing-and-testing-policies-sample"></a>若要執行醫療理賠處理和測試原則範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*> \Business Rules\Medical 理賠處理和測試 Policies\RulesForMedicalClaims\bin\Debug\  
  
2.  在命令列上執行檔案 RulesForMedicalClaims.exe。  
  
    > [!NOTE]
    >  您可以變更範例理賠申請檔案 sampleClaim.xml 中的個別項目值，重複執行範例。 下列清單中會顯示不同項目值的預期輸出。  
  
 根據所提交的範例理賠申請檔案中的各種組合值，輸出實例如下：  
  
-   對於金額超過 $1000 的理賠申請，會取得下列輸出：  
  
    ```  
    Status:  REJECTED!  
    Reason:  Amount of claim has exceeded Policy limit  
    ```  
  
-   對於住院天數超過 10 的理賠申請，會取得下列輸出：  
  
    ```  
    Status:  REJECTED!  
    Reason:  Amount of Nights has exceeded Policy limit  
    ```  
  
-   對於日期無效 (日期 > 目前日期) 的理賠申請，會取得下列輸出：  
  
    ```  
    Status:  REJECTED!  
    Reason:  Cannot submit claims for future dates!  
    ```  
  
-   對於原則識別碼不是有效的理賠申請 (例如，藉由變更**識別碼**有值為 2 的項目) 因為原則到期日，而取得下列輸出：  
  
    ```  
    Sending to Renewal Department for Customer Smir with Policy # 2  
    Status:  REJECTED!  
    Reason:  Policy ID is invalid  
    ```  
  
-   對於有效的理賠申請，會取得下列輸出：  
  
    ```  
    Status:  Claim Accepted!  
    Reason:  
    ```  
  
    > [!NOTE]
    >  每次您執行這個範例時，都會在資料夾 ...\RulesForMedicalClaims\bin\Debug 中建立文字檔 outputtrace.txt。 它包含規則執行的偵錯追蹤，每個執行循環之後都會在資料夾 \RulesForMedicalClaims\bin\Debug 中建立。 您可以檢查這個檔案來查看規則執行的追蹤輸出。  
  
## <a name="comments"></a>註解  
 評估規則集時，所使用的事實來源如下：  
  
-   長期事實擷取器。以網路為基礎的應用程式可實作**IFactReriever**介面、 建立資料夾 FactRetrieverForClaimsProcessing 中。 醫療理賠處理原則會使用它從 PolicyValidity 資料庫擷取資料 (資料集格式)，用於評估規則條件。  
  
-   宣告是 XML 文件包含下列資訊，儲存在同層級項目表單中： 名稱、 識別碼、 Amount、 Nights 和日期。  
  
-   A。以網路為基礎的類別庫 (Claims) 與**ClaimResults**類別用來記錄的狀態和原因使用屬性的宣告，以及傳送線索 （如果原則不是有效的） 叫用**SendLeads**具有識別碼和名稱做為參數的方法。  
  
 根據這些事實來源，您可以將針對此實例所定義的規則非正式地描述如下：  
  
1.  檢查輸入的理賠申請是否有效。 如果理賠申請金額超過允許的上限、如果原則已過期 (可檢查資料庫資料表來驗證)、如果住院天數超過允許的上限，而且如果理賠申請的日期是在未來，則理賠申請無效。 如果判斷理賠申請無效，則適當地設定理賠申請的 STATUS 和 REASON。  
  
2.  如果輸入的理賠申請的原則識別碼已過期，則傳送線索給原則更新部門 (並附上原則識別碼和客戶名稱)。  
  
3.  如果理賠申請有效，則適當地設定理賠申請的 STATUS 和 REASON。  
  
 規則及其條件繫結的正式表示如下：  
  
-   **規則 1。數量檢查**  
  
    ```  
    IF Amount in the XML document is > 1000  
      AND  
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"\  
         &&  
         Claims.ClaimResults.Reason = "Amount of claim has exceeded limit"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   **規則 2。花費在醫院住院**  
  
    ```  
    IF number of nights in the XML document is > 10  
      AND  
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"  
         &&  
         Claims.ClaimResults.Reason = "Amount of claim has exceeded limit"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   **規則 3。日期有效性**  
  
    ```  
    IF date on the incoming XML claim is > Today  
      AND   
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"  
         &&  
         Claims.ClaimResults.Reason = "Cannot submit claims in the future!"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   **規則 4。原則有效性**  
  
    ```  
    IF Policy is invalid for the ID in the XML claim (check database)  
      AND  
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"  
         &&  
         Claims.ClaimResults.Reason = "Policy Invalid"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   **規則 5。潛在客戶**  
  
    ```  
    IF Claim.ClaimResults.Reason = "Policy invalid"  
  
    THEN send a lead to the policy department by invoking the function Claim.ClaimResults.SendLead with customer ID and Name from the incoming XML document.  
  
    ```  
  
-   **規則 6。接受的宣告**  
  
    ```  
    IF Claim.ClaimResults.Status = null  
  
    THEN Set the claim status to be valid  
         &&  
         Send the lead to the sales department  
  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [商務規則 （BizTalk Server 範例資料夾）](../core/business-rules-biztalk-server-samples-folder.md)