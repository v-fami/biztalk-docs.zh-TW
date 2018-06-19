---
title: 設定後援本機主機設定 （EDIFACT 交易集設定） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0142b3fc-009f-4da5-b34d-dddf4fb96e0f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 931db62edda264a6fff0ddb422bd41b243cd29ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232958"
---
# <a name="configuring-fallback-local-host-settings-edifact-transaction-set-settings"></a>設定後援本機主機設定 (EDIFACT 交易集設定)
為了處理內送的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必須要判斷它需要用來處理和驗證該交換的結構描述。 這個過程包括判斷與該結構描述相關聯的目標命名空間，以及判斷要使用的結構描述。 您要在這頁後援協議中，輸入要用來判斷上述目標命名空間的屬性。 BizTalk Server 如何判斷結構描述中描述[協議解析、 結構描述探索和授權接收 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-local-host-settings-for-transaction-sets"></a>若要設定交易集的本機主機設定  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。  
  
2.  在**EDIFACT 後援設定**對話方塊中，於**EDIFACT 協議頁面**索引標籤，下方**交易集設定**區段中，按一下**本機主機設定**。  
  
3.  選取**建立針對尾端分隔符號的空 XML 標記**將交換傳送者包含尾端分隔符號的空 XML 標記。  
  
4.  選取**使用點 （.） 做為小數分隔符號**BizTalk Server 以啟用含小數的交換建立 XML 訊息中包含點 （.）。  
  
5.  如**目標命名空間**、 輸入 （或從下拉式清單中選取） 目標命名空間的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會使用來決定處理所接收的訊息之結構描述  
  
6.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [EDIFACT 後援協議屬性設定為交易集設定](../core/configuring-edifact-fallback-agreement-properties-for-transaction-set-settings.md)