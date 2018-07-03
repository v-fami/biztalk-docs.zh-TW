---
title: 如何設定每個執行個體管線屬性，如接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, properties
- receive locations, configuring
- managing [pipelines], properties
- managing [pipelines], receive locations
- managing [receive locations], pipelines
- managing [pipelines], configuring
- pipelines, receive locations
- pipelines, configuring
- receive locations, pipelines
- managing [receive locations], configuring
ms.assetid: e1ed3b10-2f39-479b-a3e6-22b4b2872192
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27c591e7ea30dd97b116f89c3d50d03ea48392b4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982415"
---
# <a name="how-to-configure-per-instance-pipeline-properties-for-a-receive-location"></a>如何設定接收位置的個別執行個體管線屬性
本主題描述如何在將管線部署到 BizTalk 群組後，使用 BizTalk Server 管理主控台來設定接收位置的管線屬性。 您所做的變更只會覆寫這個接收位置的預設管線屬性，因此您也可以為 BizTalk 群組中的每個接收位置設定不同的管線屬性。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
> [!NOTE]
>  使用每個執行個體管線屬性設定的值時**DocumentSpecNames** XML 解譯器元件的管線，指定的文件結構描述和管線中的屬性必須定義相同的專案中。  
  
### <a name="to-configure-per-instance-pipeline-properties-for-a-receive-location"></a>設定接收位置的個別執行個體管線屬性  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理]**，展開包含要設定管線屬性中，展開 [接收位置的 BizTalk 群組**應用程式**，然後展開包含該接收位置的應用程式。  
  
3. 按一下 **接收位置**資料夾中，以滑鼠右鍵按一下接收位置，然後**屬性**。  
  
4. 按一下右邊的省略符號 （...）**接收管線** 方塊中。  
  
5. 設定的屬性，然後按**確定**。 如需詳細資訊，請按一下**協助**內容 頁面上。  
  
   > [!IMPORTANT]
   >  請確定您已輸入管線屬性的正確資訊。 如果輸入無效的值 (例如，輸入字串而非數字)，將會產生錯誤。  
  
6. 如果這是要求-回應接收位置，按一下右邊的省略符號 （...）**傳送管線** 方塊中。  
  
7. 設定的屬性，然後按**確定**兩次。 如需詳細資訊，請按一下**協助**內容 頁面上。  
  
## <a name="see-also"></a>另請參閱  
 [管理管線](../core/managing-pipelines.md)   
 [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)   
 [管理接收位置](../core/managing-receive-locations.md)