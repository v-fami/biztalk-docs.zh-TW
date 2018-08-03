---
title: 處理使用商務規則 （BizTalk Server 範例） 貸款 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, business rules
- business rules, examples
ms.assetid: 3e1c80c6-adc1-4a0f-83fd-409ce1b8f21f
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1b8b1ae132d095ec70a22b8480818a0b8a11ece
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998527"
---
# <a name="loans-processing-using-business-rules-biztalk-server-sample"></a>貸款處理使用商務規則 （BizTalk Server 範例）
「使用商務規則處理貸款」範例將示範如何使用協調流程內管理的規則集，以及如何使用稱為「事實」的輸入組合，計算所處理文件內某些欄位的設定。 事實可以是呼叫 .NET 架構組件的結果，從訊息的 XML 擷取的值，或是從資料庫擷取的資料。 此範例還會示範，如何隨時變更規則來影響後續計算，而不需重新部署。  

## <a name="what-this-sample-does"></a>此範例的用途  
 此範例將使用簡化的貸款處理實例內容示範這些功能。 BizTalk Server 協調流程會選取並處理 XML 訊息格式的貸款申請，亦稱為貸款案件。 此協調流程會使用「商務規則引擎」根據規則評估內送訊息、透過套用規則的結果修改訊息，然後將訊息做為檔案寫入輸入資料夾中。  

 根據從數個來源，包括正在處理的訊息事實這個範例會設定**IncomeStatus**， **CommitmentsStatus**， **EmploymentStatus**，和**ResidencyStatus**正在處理的訊息的項目。  

## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*範例路徑*\>\Business Rules\Loans 處理使用商務 Rules\  

 下表顯示此範例中的檔案，並描述其用途。  


|                                                                                    檔案                                                                                    |                                                                                                                描述                                                                                                                 |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                   Case.xsd                                                                                    |                                                                                 內送貸款申請的結構描述檔，亦稱為貸款案件。                                                                                  |
|                                                                                  Cleanup.bat                                                                                  |                   用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。 移除傳送埠和接收埠。 視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。                   |
|                                                                           Create_CustInfo_Table.sql                                                                           |                                                                              SQL 指令碼，用於建立 SQL Northwind 範例資料庫中的 CustInfo 資料表。                                                                              |
|                                                                           LoanProcessorBinding.xml                                                                            |                                                                                               用於自動化設定，例如連接埠繫結。                                                                                               |
|                                                                   LoansProcessor.btproj、LoansProcessor.sln                                                                   |                                                                                            此範例的 BizTalk 專案和方案檔。                                                                                             |
|                                                                             My Sample Service.odx                                                                             |                                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 此範例的協調流程。                                                              |
|                                                                                sampleLoan.xml                                                                                 |                                                               範例輸入檔，其中 XML 結構結尾的四個狀態項目未包含值。                                                               |
|                                                                                   Setup.bat                                                                                   |                                                                                                 用來建置和初始化此範例。                                                                                                  |
|         在 \CreateRules 資料夾中：<br /><br /> App.ico、AssemblyInfo.cs、Case.xsd、CreateLoanProcessingPolicy.csproj、CreateLoanProcessingPolicy.sln、WriteToBRL.cs          | Visual C# 專案、方案、原始程式及相關檔案，用來建立以程式設計方式建立規則集中各項規則的應用程式。 如需以程式設計方式建置的規則集範例，請參閱原始程式檔 WriteToBRL.cs。 |
| 在 \myFactRetriever 資料夾中：<br /><br /> AssemblyInfo.cs<br /><br /> FactRetrieverForLoansProcessing.cs<br /><br /> myFactRetriever.csproj<br /><br /> myFactRetriever.sln |                 Visual C# 專案、方案、原始程式集相關檔案，用來建立從之前新增至 Northwind 範例 SQL Server 資料庫中的 CustInfo 資料表擷取資訊的組件。                  |

## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  

#### <a name="to-build-and-initialize-the-loans-processing-using-business-rules-sample"></a>建置和初始化使用商務規則的貸款處理範例  

1. 確定您的電腦上已安裝 Northwind 資料庫。  

   > [!IMPORTANT]
   >  若要執行此範例中，您必須具有 Northwind SQL Server 範例資料庫。 [下載](https://www.microsoft.com/download/details.aspx?id=23654)，並安裝。 

2. 在命令視窗中，瀏覽至下列資料夾：  

    \<*範例路徑*\>\Business Rules\Loans 處理使用商務規則  

3. 執行檔案 Setup.bat，這會執行下列動作：  

   - 清除 GAC 以便刪除之前執行此範例所留下的資料。  

   - 編譯及部署事實擷取器程式 myFactRetreiever.dll。  

   - 使用 SQL 指令碼檔案 Create_CustInfo_Table.sql、將名為 CustInfo 的資料表新增至 Northwind 範例 SQL 資料庫。  

   - 清除共用 SQL 規則存放區，以便刪除之前執行此範例所留下的資料。  

   - 建立、發佈及部署貸款處理規則集的最新版本 (1.0)。  

     > [!NOTE]
     >  您可以使用商務規則編輯器工具隨附[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]檢查以程式設計方式設定的規則。  

   - 建立此範例的輸入 (In) 和輸出 (Out) 資料夾。  

   - 編譯及部署此範例的其餘 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案，包括含有用來協調此範例之協調流程的 BizTalk 專案。  

   - 建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。  

     > [!NOTE]
     >  這個範例會在建立和繫結連接埠時顯示下列警告：  
     >   
     >  `Warning: Receive handler not specified for receive location "LoansProcessor_1.0.0.0_LoansProcessor.My_Sample_Service_Incoming_ReceiveLocation"; updating with first receive handler with matching transport type.`  
     >   
     >  `Warning: Host not specified for orchestration "LoansProcessor.My_Sample_Service"; updating with first available host.`  
     >   
     >  您可以安全地忽略這些警告。 (繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。  

   - 啟用接收位置並啟動傳送埠。  

   - 登錄並啟動協調流程。  

> [!NOTE]
>  如果您的 BizTalk 主控件名稱不是 BizTalkServerApplication，請修改 Setup.bat 檔和 LoanProcessorBinding.xml 檔以反映正確的主控件名稱。  
> 
> [!NOTE]
>  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。  
> 
> [!NOTE]
>  若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 使用此金鑰組簽署所產生的組件。  
> 
> [!NOTE]
>  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  

## <a name="running-this-sample"></a>執行此範例  

#### <a name="to-run-the-loans-processing-using-business-rules-sample"></a>執行使用商務規則處理貸款範例  

1. 貼上到 sampleLoan.xml 檔的複本**\In**資料夾。  

2. 觀察資料夾中建立的.xml 檔案**出**。它包含輸入的 XML 訊息新增至下列四個狀態元素的 XML 結構結尾的資料： **IncomeStatus**， **CommitmentsStatus**， **EmploymentStatus**，並**ResidencyStatus**。  

   您可以使用「商務規則編輯器」工具變更規則集中的規則，然後重新部署這些規則。  

#### <a name="to-use-the-business-rule-composer-tool-to-change-one-or-more-of-the-rules-in-a-rule-set"></a>使用商務規則編輯器工具變更規則集中的一或多項規則  

1. 按一下 **開始**，指向**程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**商務規則編輯器 」**。  

   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。 若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。  

2. 在 [ **SQL Server** ] 對話方塊中，按一下 **[確定]** 連接至規則存放區。  

3. 在 [**原則總管]**，節點底下**LoanProcessing**，以滑鼠右鍵按一下**1.0 版 – 已部署**節點，然後再按一下**複製**。  

4. 以滑鼠右鍵按一下**LoanProcessing**，然後按一下**貼上**。  

5. 變更任何規則或動作，將會導致不同的值的方式**IncomeStatus**， **CommitmentsStatus**， **EmploymentStatus**，和**ResidencyStatus**項目。 請確定您也變更負數部份的值 (基本上， **Else**子句) 的任何您選擇變更的規則。  

    下表顯示此範例使用的規則集。 除非有另外特別說明，否則事實會來自內送 XML 訊息。 字串 (db) 表示，事實的來源為資料庫。  


   |  規則號碼   |        規則名稱        |                                                                             描述                                                                             |
   |----------------|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |       @shouldalert        |   Income Status Rule    |                                       如果**BasicSalary** + **OtherIncome** > 0<br /><br /> 然後**IncomeStatus** = **有效**                                        |
   |       2        | Commitments Status Rule | 如果**識別碼** == **識別碼 (db)**<br /><br /> 與<br /><br /> 如果**CreditCardBalance (db)** > 500<br /><br /> 然後**CommitmentsStatus** =<br /><br /> "Compute Commitments" |
   |       3        | Employment Status Rule  |                                  如果**EmploymentType &#124; TimeInMonths** > 18<br /><br /> 然後**EmploymentStatus** = **有效**                                   |
   |       4        |  Residency Status Rule  |                                  如果**PlaceOfResidence &#124; TimeInMonths** > 18<br /><br /> 然後**ResidencyStatus** = **有效**                                  |
   | !1, !2, !3, !4 |     Negation Rules      |    條件的邏輯**不**對應規則 1 – 4 中所述的條件。 結果動作為所設定字串的變更。     |


6. 以滑鼠右鍵按一下**1.1 （未儲存） 版**節點，然後再按一下**儲存**。  

7. 以滑鼠右鍵按一下**1.1 版**節點，然後再按一下**發佈**。  

8. 以滑鼠右鍵按一下**1.1 版**節點，然後再按一下**部署**。  

9. 等候 60 秒，讓變更傳播到共用 SQL Server 規則存放區。  

10. 將 sampleLoan.xml 檔的複本貼到資料夾**在**。  

11. 觀察資料夾中建立的.xml 檔案**出**。它包含輸入的 XML 訊息新增至下列四個狀態元素的 XML 結構結尾的資料： **IncomeStatus**， **CommitmentsStatus**， **EmploymentStatus**，並**ResidencyStatus**。 視此程序步驟 5 中所做的變更本質而定，新增至這些項目的資料可能會與上一次執行時的資料不同。  

## <a name="comments"></a>註解  
 如果您要檢視此範例的追蹤資訊，您必須使用 [商務規則引擎部署精靈] 解除部署再重新部署相關的規則集 (貸款處理)。  

 此範例將示範如何使用商務規則，在協調流程內以規則的形式套用商務原則。 此外還會示範如何變更原則，以及在協調流程中動態反映原則的變更，而不需重新編譯或重新部署協調流程方案。  

 此範例的輸入貸款案件是 XML 訊息，其結構如下：  

```  
    Name  
    ID  
    Income  
        BasicSalary  
        OtherIncome  
    EmploymentType  
        TimeInMonths  
    PlaceOfResidence  
        TimeInMonths  
    CommitmentsStatus  
    IncomeStatus  
    EmploymentStatus  
    ResidencyStatus  
```  

## <a name="see-also"></a>另請參閱  
 [商務規則 (BizTalk Server Samples 資料夾)](../core/business-rules-biztalk-server-samples-folder.md)