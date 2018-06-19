---
title: 步驟 1： 建立服務匯流排命名空間 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ede1ac50-bbfb-4aeb-8217-1877ae218f89
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4d7630316f72fd63bac5ce7127b5451683e2f97
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276758"
---
# <a name="step-1-create-a-service-bus-namespace"></a>步驟 1： 建立服務匯流排命名空間
在此步驟中，您會建立[!INCLUDE[winazure](../includes/winazure-md.md)][!INCLUDE[sb](../includes/sb-md.md)]命名空間。 您將使用此命名空間來裝載接收來自 Salesforce 的商機通知的轉送端點。 稍後在建立此方案，您會使用這個轉送端點來接收通知訊息至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。  
  
### <a name="to-create-a-includesbincludessb-mdmd-namespace"></a>若要建立[!INCLUDE[sb](../includes/sb-md.md)]命名空間  
  
1.  登入[http://manage.windowsazure.com](http://manage.windowsazure.com)使用您的 Microsoft 帳戶。  
  
2.  在頁面底部，按一下**新增**，**應用程式服務**， **Service Bus 轉送**，然後**快速建立**。  
  
3.  輸入的命名空間為`BtsSalesforce`，然後選取最接近您目前的地理位置區域。 按一下**建立轉送**。  
  
    > [!CAUTION]
    >  此命名空間必須是全域唯一的。 因此，您必須使用在本教學課程提到以外的命名空間。  
  
    > [!NOTE]
    >  請注意，轉送不會建立作業的一部分，此命名空間。 當我們設定的接收位置的轉送端點建立稍後在本教學課程**Sb-messaging**配接器。  
  
4.  建立命名空間之後，狀態也設為**Active**。 作用中狀態之後，您可以選取的命名空間，然後按一下**便捷鍵**頁面以取得詳細資料，如何連接到底部**BtsSalesforce**命名空間，包括值**預設使用者**和**預設金鑰**。 稍後在本教學課程中，您將需要這些詳細資料。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 6： 與 Salesforce 整合 BizTalk Server 2013](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)