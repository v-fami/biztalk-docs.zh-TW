---
title: 將 PeopleSoft 結構描述匯入 Visual Studio |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 411f25f4-4431-44e4-84cf-5c515b3e32db
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6af82459f8b51f3dfa73a52593db18d25365c2a
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013533"
---
# <a name="import-peoplesoft-schemas-into-biztalk-server-projects"></a>PeopleSoft 結構描述匯入至 BizTalk Server 專案
當您建立 PeopleSoft Enterprise 系統後，可以瀏覽伺服器並將結構描述匯入至 BizTalk Server 專案。  
  
## <a name="browse-a-peoplesoft-server-system"></a>瀏覽 PeopleSoft 伺服器系統  
  
1.  使用滑鼠右鍵按一下 BizTalk Server 專案，然後選取下列其中一個選項。  
  
    -   如果您已經有產生物件的結構描述，選取**新增**，按一下 **新增結構描述**，然後選取 現有的結構描述，將新增至您的協調流程。  
  
    -   如果您沒有為物件產生的結構描述，選取**新增**，然後按一下 **新增產生的項目**，然後選取 配接器。 這是相同的名稱中輸入**AdapterProperties**  對話方塊。 如需詳細資訊，請參閱 BizTalk 主要說明中的＜配接器屬性對話方塊＞。  
  
2.  按 [下一步]。  
  
     PeopleSoft Enterprise 系統就會顯示於瀏覽器中。  
  
     ![](../core/media/psad-psnewadapter-14-browsing-cominterfacess.gif "PSAd_PSNewAdapter_14_Browsing_ComInterfacess")  
  
### <a name="component-interfaces"></a>元件介面  
 在**元件介面**(CI) 資料夾中，您可以檢視所有可用的元件介面，在系統中。 元件介面會宣告它所支援的方法和屬性集合。 元件介面不會實作行為或屬性。 Microsoft BizTalk Adapter for PeopleSoft Enterprise 公開標準方法，例如 CreateEx、DeleteOnly、Find、Get 與 UpdateEx。 如需這些方法的說明，請參閱[附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md)。  
  
## <a name="generate-schemas"></a>產生結構描述  
  
選取您要匯入結構描述的項目：**訊息**，**查詢**，或**元件介面**。  BizTalk Server 會為選取的項目產生結構描述，並將它們匯入至 BizTalk Server 專案。  
  
> [!NOTE]
>  如果伺服器物件定義變更，您必須重新產生結構描述以更新其中包含的資料。  
  
## <a name="see-also"></a>另請參閱  
 [建立 PeopleSoft 傳送處理常式](../core/creating-peoplesoft-send-handlers.md)