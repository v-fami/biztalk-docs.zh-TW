---
title: 手動指定新的主要密碼伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3fa44143-8d29-49ba-9c71-96be2c9ded67
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b6d635312d3765c37f1ab9c2b64505698f93e5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299798"
---
# <a name="designating-a-new-master-secret-server-manually"></a>手動指定新的主要密碼伺服器
叢集硬體費不貲。 如果硬體成本是一項考量，您可以考慮手動指定期間所要主要密碼伺服器失敗的情況下的另一個企業單一登入 (SSO) 伺服器。 使用此選項，SSO 群組中的其他 SSO 伺服器可提升為主要密碼伺服器。 當主要已關閉時，您可以手動升級其中一部 SSO 伺服器，為主要密碼伺服器。 這項技術的最大的缺點是，您無法編輯現有的部署，重新啟動現有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務，或部署新的 BizTalk 應用程式，直到您升級新的主要密碼伺服器。  
  
 若要進行無縫式的程序，您必須實作某些監視的機制，讓您將儘速探索失敗。 您也可以使用監視的應用程式，例如 System Center Operations Manager，以自動化升級程序。  
  
 如需有關以手動方式將主要密碼伺服器的詳細資訊，請參閱[如何移動主要密碼伺服器](http://go.microsoft.com/fwlink/?LinkId=156841)(http://go.microsoft.com/fwlink/?LinkId=156841) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
## <a name="see-also"></a>另請參閱  
 [叢集主要密碼伺服器](../technical-guides/clustering-the-master-secret-server.md)