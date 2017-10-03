---
title: "單一登入規劃 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d1bc220-4087-4603-ac15-6bb0c62c59d4
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bc35c53193ac8e48c9169131b637dc1d7a581fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-single-sign-on"></a>規劃 單一登入
企業單一登入 (SSO) 時的重要元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行的階段無法運作，而 SSO 服務，因為所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器組態資訊會加密並儲存在 SSO 資料庫和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]存取這項資訊透過 SSO 服務。 如果 SSO 服務不會執行 BizTalk server 上，或如果 SSO 服務並沒有 SSO 主要密碼伺服器的存取，不能存取此配接器組態資訊。  
  
 SSO 實作應該包含下列的計劃。  
  
## <a name="backing-up-the-master-secret"></a>備份主要密碼  
 如果 SSO 主要密碼伺服器失敗且遺失金鑰，或者是金鑰損毀，您將無法擷取儲存在 SSO 資料庫中的資料。 您必須備份主要密碼，否則會有遺失 SSO 資料庫資料的風險。 因此務必絕對 SSO 主要密碼已備份，以及儲存在安全的位置。 如需 SSO 主要密碼備份的詳細資訊，請參閱[如何重新設定主要密碼](http://go.microsoft.com/fwlink/?LinkId=151395)(http://go.microsoft.com/fwlink/?LinkId=151395)。  
  
## <a name="configuring-sso-for-high-availability"></a>設定 SSO 的高可用性  
 因為 SSO 是讓這類的重要元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，SSO 主要密碼伺服器應設定為高可用性。 如果可能的話，應該叢集企業單一登入服務主要密碼伺服器上的依照下列中的步驟[叢集主要密碼伺服器](../technical-guides/clustering-the-master-secret-server.md)。 您無法存取 Windows Server 叢集，所以您仍然可以提供企業單一登入服務主要密碼伺服器上的高可用性依照主題中說明的步驟[指定新的主機密碼伺服器手動](../technical-guides/designating-a-new-master-secret-server-manually.md)。  
  
## <a name="following-established-sso-security-recommendations"></a>下列已建立的 SSO 安全性建議  
 請依照下列主題所述的 SSO 安全性建議[SSO 安全性建議](http://go.microsoft.com/fwlink/?LinkId=155753)(http://go.microsoft.com/fwlink/?LinkId=155753)。