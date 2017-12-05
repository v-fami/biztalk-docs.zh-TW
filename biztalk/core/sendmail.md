---
title: "SendMail |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SMTP adapters, examples
- examples, SMTP adapters
- SMTP adapters
ms.assetid: a0258619-b195-4c8a-8326-77add6e6f04d
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6cf0243eccb6a38dc121cfe06a60e30fa0c26c7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="sendmail"></a>SendMail
SendMail 範例示範如何使用 Simple Mail Transfer Protocol (SMTP) 配接器，從 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程內傳送電子郵件訊息。 用來傳送電子郵件訊息的動態資訊，會使用以屬性升級功能從 XML 訊息擷取。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例會依下列步驟順序，從內送 XML 訂單 (PO) 訊息升級而來的屬性取得資訊，再使用該項資訊傳送電子郵件訊息：  
  
1.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程擷取輸入 XML PO 訊息。  
  
2.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協調流程升級**PONumber**和**電子郵件**將來更容易存取的屬性。  
  
3.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程，使用升級屬性的值來設定動態傳送埠的目的地址和電子郵件訊息的主旨。  
  
4.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程透過 SMTP 配接器傳送所建構的電子郵件訊息。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*範例路徑*\>\AdaptersUsage\SendMail\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|AssemblyInfo.cs, SendMail.btproj, SendMail.sln|提供此範例的專案、解決方案和組件資訊檔案。|  
|Cleanup.bat|從全域組件快取 (GAC) 解除部署並移除組件；移除傳送和接收埠；視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|PropertySchema.xsd, PurchaseOrder.xsd|分別針對您要升級的屬性和 XML PO 訊息提供結構描述。|  
|ReceiveSend.odx|提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程，以處理內送 XML PO 訊息，並根據訊息內的資訊傳送電子郵件訊息。|  
|SendMailInput.xml|包含範本輸入檔，其中包含使用 XML 指定的訂單。|  
|Setup.bat|建置並初始化此範例。 **注意：**和此安裝程式檔案建立並繫結連接埠，依此類推，使用不同的機制，比大多數的安裝程式檔案的 SDK 範例。 並不需要附贈 .xml 檔案。|  
  
### <a name="to-build-and-initialize-this-sample"></a>若要建置並初始化這個範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*\>\AdaptersUsage\SendMail  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   為此範例建立下列輸入資料夾：  
  
         \<*範例路徑*\>\AdaptersUsage\SendMail\In  
  
    -   為此範例編譯 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  
  
    -   啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。  
  
        > [!NOTE]
        >  在嘗試執行此範例之前，您必須確認 BizTalk 沒有在建置和初始化的程序中報告任何錯誤。  
  
        > [!NOTE]
        >  如果您在此範例中選擇開啟並建置專案，而不執行檔案 Setup.bat，必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 請使用這個金鑰組來簽署產生的組件。  
  
        > [!NOTE]
        >  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat 並刪除所有前置詞為 SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail 的接收埠和傳送埠。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
3.  在**BizTalk Server 管理**主控台中，尋找前置詞為 SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail 的接收埠。 更新此接收埠的接收位置，以指向檔案系統上做為輸入位置的目錄。  
  
4.  使用 [記事本] 之類的程式來修改檔案 SendMailInput.xml，讓**電子郵件**項目會指定要接收此範例所產生的電子郵件訊息的合法電子郵件地址。  
  
5.  按一下**啟動**，指向 **程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
6.  在**BizTalk Server 管理**主控台中，展開 BizTalk 群組樹狀結構。  
  
7.  展開**平台設定**樹狀目錄中的左窗格中。  
  
8.  展開**配接器**資料夾中，按一下  **SMTP**節點，然後再按兩下右窗格中的資料列的 SMTP 配接器。  
  
9. 在**SMTP-配接器處理常式屬性**對話方塊中，按一下 **屬性**。  
  
10. 在**SMTP 傳輸屬性**對話方塊**屬性**索引標籤上，提供適當的值，如**SMTP 伺服器名稱**和**（電子郵件地址）**屬性，然後再按一下**確定**。  
  
     透過此 SMTP 配接器傳送的任何電子郵件訊息，都是使用這些值來建構寄件者電子郵件地址。  
  
    > [!NOTE]
    >  若您需要驗證 SMTP 伺服器，必須確保寄件者電子郵件地址的所屬帳號與驗證所用的帳戶相同。  
  
11. 請停止再重新啟動 BizTalk 服務 ( BizTalkServerApplication )，協調流程才會採用這些變更。  
  
### <a name="to-run-this-sample"></a>執行此範例  
  
1.  將修改後之 SendMailInput.xml 檔案的複本放在 [輸入] 資料夾中。  
  
2.  請觀察您在上一個程序中指定的電子郵件地址是否接收到電子郵件訊息。  
  
## <a name="see-also"></a>請參閱  
 [配接器範例 - 用法](../core/adapter-samples-usage.md)