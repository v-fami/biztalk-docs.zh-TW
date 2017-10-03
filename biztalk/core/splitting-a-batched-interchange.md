---
title: "分割批次的交換 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e67bef19-77fb-47a9-88f3-ee20043b3691
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 745f94d4ec56222d3c1d3e03c0817933248f4b8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="splitting-a-batched-interchange"></a>分割批次交換
本主題會說明如何藉由分割交換中的交易集，來設定處理批次 EDI 交換的協議。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-receive-a-split-edi-interchange"></a>若要接收分割的 EDI 交換  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象**節點。 在**合作對象與商務設定檔**頁面上，按一下會解析為內送的批次交換的協議的合作對象。 在**協議**區段頁面上，以滑鼠右鍵按一下 在協議，按一下**屬性**。 在**協議屬性** 對話方塊中單向協議索引標籤上 （要輸入批次的交換將解析），執行下列動作：  
  
    1.  在**識別碼**頁面上，確定您輸入正確的值，讓內送的批次的交換解析成此協議。  
  
        -   如果是**X12**： 設定 ISA5、 ISA6、 ISA7 和 ISA8。  
  
        -   如果是**Edifact**： 設定 UNB2.1、 UNB2.2、 UNB3.1 和 UNB3.2。  
  
    2.  在**本機主機設定**頁面 (下**交換設定**) 下**接收者的設定** 區段中，針對**輸入批次處理選項**，選取下列選項：  
  
        -   **將交換分割為交易集-發生錯誤時暫停交易集**– 選取此選項以指定 BizTalk Server 應該剖析每個交易集在個別的 XML 文件的交換。 然後，BizTalk Server 便會將適當的信封套用至交易集，並將交易集文件路由到 MessageBox 中。 使用此選項時，如果交換中的一或多個交易集驗證失敗，BizTalk Server 將只會暫停這些交易集。  
  
        -   **將交換分割為交易集-發生錯誤時暫停交換**– 選取此選項以指定 BizTalk Server 應該剖析每個交易集在個別的 XML 文件的交換。 然後，BizTalk Server 便會將適當的信封套用至交易集，並將交易集文件路由到 MessageBox 中。 使用此選項時，如果交換中的一或多個交易集的驗證失敗，BizTalk Server 便會暫停整個交換。  
  
2.  為保留的批次建立 Visual Studio 專案，如下所示：  
  
    1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立 BizTalk 專案並針對批次內的所有訊息新增結構描述。  
  
    2.  建立及部署專案。  
  
3.  在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，建立傳送分割批次所需的傳送埠，如下所示：  
  
    1.  傳送管線設定為**EdiSend**或**AS2EdiSend**。  
  
    2.  將傳送埠的篩選條件設定為取得每個交易集的必要值，例如，設定為 BTS.MessageType。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDI 批次](../core/configuring-edi-batches.md)   
 [如何建立傳送埠](../core/how-to-create-a-send-port2.md)