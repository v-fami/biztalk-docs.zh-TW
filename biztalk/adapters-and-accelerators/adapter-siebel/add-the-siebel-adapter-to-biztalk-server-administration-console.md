---
title: "BizTalk Server 管理主控台中加入 Siebel 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b64d0bdc-ac83-46c9-b27d-625088a013d3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebb4a946c9fd987c1a97fa24a9b50d3cdf2f7d18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="add-the-siebel-adapter-to-biztalk-server-administration-console"></a>新增 Siebel 配接器至 BizTalk Server 管理主控台
[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可用於 BizTalk 作為 WCF 自訂連接埠或 Wcf-siebel 連接埠。 如果您想要使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]透過 WCF 自訂連接埠，您不需要新增 WCF 自訂連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台，因為 WCF 自訂連接埠新增到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]預設的管理主控台。 不過，如果您想要使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]透過 Wcf-siebel 連接埠，您必須先新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
 本主題說明如何新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
> [!IMPORTANT]
>  您不需要執行這些工作，如果您想要設定 WCF 自訂連接埠[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
## <a name="add-the-siebel-adapter"></a>新增 Siebel 配接器  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，依序展開**平台設定**，然後按一下 **配接器**。  
  
3.  以滑鼠右鍵按一下**配接器**，指向 **新增**，然後按一下**配接器**。  
  
     ![新增配接器](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")  
  
4.  在**配接器屬性**對話方塊方塊中，配接器和從指定名稱**配接器**清單中，選取**Wcf-siebel**。  
  
     ![加入 WCF &#45;Siebel 配接器至 BizTalk 主控台](../../adapters-and-accelerators/adapter-siebel/media/6d39b874-2233-452a-81ef-d93274b0784c.gif "6d39b874-2233-452a-81ef-d93274b0784c")  
  
5.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
[若要建立 Siebel 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)