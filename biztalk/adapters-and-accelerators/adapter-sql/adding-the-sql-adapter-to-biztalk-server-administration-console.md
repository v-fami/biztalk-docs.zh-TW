---
title: 將 SQL 配接器新增至 BizTalk Server 管理主控台 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd974f28-c9cb-46de-95be-83716231ebcd
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff3eb1aa8870316ec506a61658c34db6acc7f62c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005727"
---
# <a name="adding-the-sql-adapter-to-biztalk-server-administration-console"></a>將 SQL 配接器新增至 BizTalk Server 管理主控台
[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可用於 BizTalk 做為 WCF 自訂連接埠或 WCF SQL 連接埠。 如果您想要使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]透過 WCF 自訂連接埠，您不需要新增的 WCF 自訂連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台，因為 WCF 自訂連接埠新增至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，預設值。 不過，如果您想要使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]透過 WCF SQL 連接埠，您必須先新增 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
 本主題說明如何新增 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
> [!IMPORTANT]
>  您不需要請遵循下列步驟，如果您想要設定 WCF 自訂連接埠[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
## <a name="add-the-sql-adapter"></a>新增 SQL 配接器  
  
1. 開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 依序展開**BizTalk 群組**，展開**平台設定**，然後選取**配接器**。  
  
3. 以滑鼠右鍵按一下**配接器**，指向**新增**，然後選取**配接器**。  
  
    ![新增配接器](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")  
  
4. 在 **配接器屬性**對話方塊中，輸入名稱，該介面卡，然後從**配接器**清單中，選取**WCF-SQL**。  
  
    ![新增 WCF&#45;SQL 配接器至 BizTalk](../../adapters-and-accelerators/adapter-sql/media/4c6e2650-5d3a-4de8-a60a-a136d93a6fcf.gif "4c6e2650-5d3a-4de8-a60a-a136d93a6fcf")  
  
5. 選取 [確定]。  
  
## <a name="see-also"></a>另請參閱  
 [若要開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)