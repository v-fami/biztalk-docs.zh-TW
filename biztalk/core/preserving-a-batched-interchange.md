---
title: 保留的批次的交換 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 907e07f3-1f3e-485e-a82d-b28eb7658e0a
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 887995e9a44996c57da9e36bec1c5ec3edc1cc7b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993487"
---
# <a name="preserving-a-batched-interchange"></a>保留批次交換
本主題說明如何設定協議，以單一文件的方式處理批次 EDI 交換，而不需要分割交換中的交易集。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-the-receiving-and-sending-of-a-preserved-batch"></a>若要設定保留批次的接收和傳送  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**合作對象**節點。 在 **合作對象與商務設定檔**頁面上，按一下 已解析內送的批次交換的協議的合作對象。 在 **協議**一節的頁面上，以滑鼠右鍵按一下 協議，並按一下 **屬性**。 在 [**協議屬性**] 對話方塊中單向協議索引標籤上 （要輸入批次的交換將解析），執行下列動作：  
  
   1.  在 **識別碼**頁面上，輸入的值輸入值 ISA5、 ISA6、 ISA7 和 isa8 的值。 確定您輸入的值正確無誤，能讓內送批次交換解析成此協議。  
  
   2.  中**本機主機設定**網頁 (底下**交換設定**) 下**接收者的設定** 區段中，針對**輸入批次處理選項**，選取其中一個下列選項：  
  
       -   **保留交換-發生錯誤時暫停交換**– 選取此選項以指定 BizTalk Server 應該讓交換維持不變，建立整個批次交換的 XML 文件。 使用此選項時，如果交換中的一或多個交易集的驗證失敗，BizTalk Server 便會暫停整個交換。  
  
       -   **保留交換-發生錯誤時暫停交易集**– 選取此選項以指定 BizTalk Server 應該讓交換維持不變，建立整個批次交換的 XML 文件。 使用此選項時，如果交換中的一或多個交易集的驗證失敗，BizTalk Server 便只會暫停這些交易集，但繼續處理其他所有的交易集。  
  
       > [!NOTE]
       >  如果您選取上述兩個選項中的任一項，交換、群組和交易集區段屬性 (負責決定 BizTalk Server 如何建立外寄交換的 ISA、GS 和 ST 標頭) 即不適用。 該交換、群組，以及將保留之交換中的交易集標頭，都會在傳送管線處理該交換的傳送時加以保留。 但是，如果您想使用在協議中針對交換指定的值，請將 `EDI.PopulateInterchangeValues` 內容屬性設定為 true。  
  
2. 為保留的批次建立 Visual Studio 專案，如下所示：  
  
   1. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立 BizTalk 專案並針對批次內的所有訊息新增結構描述。  
  
   2. 建立及部署專案。  
  
3. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，建立傳送保留的批次所需的傳送埠，如下所示：  
  
   1.  若要設定傳送管線**EdiSend**或是**AS2EdiSend**。  
  
   2.  將傳送埠的篩選條件設定為內容屬性 `EDI.ReuseEnvelope == True`。  
  
       > [!NOTE]
       >  設定此篩選條件可確保傳送埠會訂閱保留的所有批次交換。 EdiReceive 接收管線會升級內容屬性 `EDI.ReuseEnvelope`，以將交換識別為保留的交換。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDI 批次](../core/configuring-edi-batches.md)   
 [如何建立傳送埠](../core/how-to-create-a-send-port2.md)