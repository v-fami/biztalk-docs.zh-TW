---
title: 在協調流程中的處理類型的錯誤合約 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- typed fault contracts [orchestrations]
- WCF services, orchestrations
- orchestrations, typed fault contracts
- orchestrations, WCF services
ms.assetid: 5a1a7d22-b0ff-4d09-bebf-4995229784b0
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bc4226b0e8f3ea5ac025f0bb7234559a52104e7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967207"
---
# <a name="how-to-handle-typed-fault-contracts-in-orchestrations"></a>如何在協調流程中處理類型錯誤的合約
本主題描述如何在使用 WCF 服務時，從協調流程內處理類型錯誤的合約。 若要處理協調流程中的類型的錯誤例外狀況，您使用的 WCF 服務必須擁有**FaultContractAttribute**套用至服務作業，因此，錯誤可能會擲回使用**FaultException**\<T\>其中 T 可以是任何有效的資料合約或可序列化的型別，從 WCF 服務。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-handle-typed-fault-contracts-in-orchestrations"></a>若要在協調流程中處理類型錯誤的合約  
  
1. 在您的 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk 專案的 [方案總管] 中以滑鼠右鍵按一下您的專案，按一下**新增**，然後按一下**加入產生的項目**。  
  
2. 在 **加入產生的項目- \<** <em>專案名稱</em>**\>** 對話方塊中，於**範本** 區段中，選取 **取用 WCF 服務**，然後按一下**新增**。  
  
3. 在 [**歡迎使用 BizTalk WCF 服務使用精靈**頁面上，按一下**下一步]**。  
  
4. 在 [**中繼資料來源**頁面上，選取**中繼資料交換 (MEX) 端點**，然後按一下**下一步]**。  
  
5. 在上**中繼資料端點**頁面上，指定執行中的服務提供透過 Ws-metadata Exchange 或 Http-get 下載的中繼資料的 URL，例如http://localhost:8005。 若要從 URL 取得中繼資料文件，請按一下**取得**。 如果執行中的服務需要基本驗證配置的使用者認證，請按一下**編輯**來開啟**BizTalk WCF 服務使用精靈**對話方塊中，您可以在其中提供的使用者名稱和若要存取執行中的服務時使用的密碼。 按 [下一步] 。  
  
6. 在 **匯入 WCF 服務中繼資料摘要**頁面上，檢閱您的設定。 您可以按一下**回**進行任何變更。 然後按一下**匯入**建立的 BizTalk 成品和用於使用 WCF 服務的型別。  
  
7. 在 **完成 BizTalk WCF 服務使用精靈**頁面上，按一下**完成**。  
  
8. 假設您使用的 WCF 服務擲回下列錯誤例外狀況：  
  
   ```  
   throw new FaultException<MyOperationException>(divideException);  
   ```  
  
    傳送埠上的錯誤作業預期類型的訊息**MyOperationException**，但 WCF 回應訊息包含完整錯誤內文。 因此，您需要擷取**MyOperationException**從藉由設定訊息部分**輸入 BizTalk 訊息內文**在傳輸屬性 對話方塊中的選項。 例如，  
  
   -   選取 **路徑--內容由內文路徑定位**。  
  
   -   將內文路徑運算式設定如下：  
  
       ```  
       /*[local-name()='Fault']/*[local-name()='Detail']/* | /*[local-name()='DivideResponse']  
       ```  
  
   -   選取  **Xml**從**節點編碼**下拉式清單。  
  
9. 在協調流程中，您必須新增範圍和兩個例外狀況處理常式。 例外狀況處理常式是錯誤 」 作業，類似於**MyOperationException**上述範例中，所示的其他例外狀況處理常式會攔截泛型**SOAPExceptions**。  
  
## <a name="see-also"></a>另請參閱  
 [如何從協調流程發佈為 WCF 服務擲回錯誤例外狀況](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md)   
 [如何使用 BizTalk WCF 服務使用精靈來取用 WCF 服務](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md)