---
title: 新增 SAP 配接器至 BizTalk Server 管理主控台 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 95fc925d-0aac-4f0d-a19d-ad27469e4b3c
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19870e69dc502f9635f34b578c2853aaf8897e00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216038"
---
# <a name="add-the-sap-adapter-to-biztalk-server-administration-console"></a>新增 SAP 配接器至 BizTalk Server 管理主控台
[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可用於 BizTalk 作為 WCF 自訂連接埠或 WCF SAP 連接埠。 如果您想要使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]透過 WCF 自訂連接埠，您不需要新增 WCF 自訂連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台，因為 WCF 自訂連接埠新增到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]預設的管理主控台。 不過，如果您想要使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]透過 WCF SAP 連接埠，您必須先新增 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
 本主題提供有關如何加入 WCF SAP 配接器，以指示[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
> [!IMPORTANT]
>  您不需要執行這些工作，如果您想要設定 WCF 自訂連接埠[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="add-the-sap-adapter"></a>新增 SAP 配接器  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，依序展開**平台設定**，然後按一下 **配接器**。  
  
3.  以滑鼠右鍵按一下**配接器**，指向 **新增**，然後按一下**配接器**。  
  
     ![新增配接器](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")  
  
4.  在**配接器屬性**對話方塊方塊中，配接器和從指定名稱**配接器**清單中，選取**WCF SAP**。  
  
     ![新增 SAP 配接器至 BizTalk](../../adapters-and-accelerators/media/a1235b38-ab93-4233-924d-42710540b951.gif "a1235b38-ab93-4233-924d-42710540b951")  
  
5.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
[若要建立的 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)