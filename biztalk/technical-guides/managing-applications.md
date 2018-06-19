---
title: 管理應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef1039fb-7460-444b-a45e-2783bdc7c109
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52e525499671a04228763c6792961c3204a3a2d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298670"
---
# <a name="managing-applications"></a>管理應用程式
BizTalk 應用程式是應用程式成品，例如協調流程、 管線、 結構描述、 對應和連接埠的邏輯容器。 BizTalk 應用程式可讓您在相同的容器中包含相關的元件。 在應用程式內的任何成品可能會在該應用程式的其他成品，或任何參考的應用程式中的任何成品參考。 如需可以在 BizTalk 應用程式的成品的完整清單，請參閱[什麼是 BizTalk 應用程式？](http://go.microsoft.com/fwlink/?LinkId=154994) (http://go.microsoft.com/fwlink/?LinkId=154994)。  
  
 BizTalk 應用程式簡化許多每天[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]工作。 部署、 管理、 啟動、 停止時，即可疑難排解[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式層級。 如此可避免混淆與較低的使用者錯誤的風險。 包含 BizTalk 應用程式容器  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Visual Studio 環境部署至它的組件。 應用程式也可能包含接收埠、 接收位置、 傳送埠，屬性的追蹤設定，與角色連結。 您可以手動新增[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式，或移動的組件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]從其他應用程式的組件。 此外，您可以加入非[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組件和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]成品，例如商務規則引擎 (BRE) 原則和 BAM 定義檔案。 以隱含方式，應用程式也包含所有目前的設定都由繫結。  
  
 您可以建立前置或後置處理指令碼來執行動作，匯入應用程式時，安裝或解除安裝。 如需有關如何使用這類指令碼的詳細資訊，請參閱[使用前置和後置處理指令碼，以自訂應用程式部署](http://go.microsoft.com/fwlink/?LinkId=154995)(http://go.microsoft.com/fwlink/?LinkId=154995)。  
  
 本節說明如何部署版本，及更新應用程式或個別成品。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [部署應用程式](../technical-guides/deploying-an-application.md)  
  
-   [更新應用程式](../technical-guides/updating-an-application.md)