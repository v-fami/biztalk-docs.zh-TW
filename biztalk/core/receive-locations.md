---
title: 接收位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive locations, properties
- receive locations, about receive locations
- receive locations
- receive locations, receive location types
ms.assetid: be5f7e5d-b63f-42f6-985e-895ba3912d34
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9866edd5dfa6f953c4e847f191891bd7e6bc25ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268622"
---
# <a name="receive-locations"></a>接收位置
建立接收位置牽涉到指定輸入訊息會送達的位址，而處理訊息的傳訊管線也會在該位址處理訊息。 只有系統管理員可以建立和啟用接收位置。  
  
 系統管理員可以使用 BizTalk 管理主控台來建立接收位置、將接收位置繫結至協調流程、啟用接收位置、停用接收位置，以及設定接收位置的全域屬性。  
  
 使用 BizTalk 管理主控台的系統管理員會依照下列步驟來建立接收位置：  
  
1.  建立接收位置。  
  
2.  將接收位置與主控件產生關聯。  
  
3.  將接收位置繫結到協調流程。  
  
4.  啟用接收位置。  
  
5.  接收位置接收訊息。  
  
> [!NOTE]
>  使用 Windows Management Instrumentation (WMI) 對接收位置所做的變更，會影響 BizTalk 管理主控台中顯示接收位置的情形。 例如，如果系統管理員使用 WMI 建立新的接收位置，該接收位置就會出現在 BizTalk 管理主控台中。 同樣地，若系統管理員刪除接收位置，該接收位置就會在 BizTalk 管理主控台中消失。  
  
> [!IMPORTANT]
>  每個接收位置都必須有一個唯一的名稱。 兩個接收位置不能有相同的名稱，在同一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。  
  
> [!IMPORTANT]
>  建議您在接收位置的放置位置中設定強式存取控制清單 (ACL)。 例如，您必須在檔案接收位置拾取訊息的目錄中設定強式 ACL，讓只有經過授權的使用者可以在此位置放置訊息。  
  
## <a name="receive-location-types"></a>接收位置類型  
 接收位置有兩種類型  
  
-   單向。 用在應用程式放置訊息但不等候同步回覆時。  
  
-   要求-回應。 用在應用程式需要訊息的回應時。  
  
## <a name="receive-location-properties"></a>接收位置屬性  
 接收位置具有全域屬性與配接器特有的屬性。 使用 BizTalk 管理主控台的系統管理員，可設定所有與特定配接器相關的接收位置的全域屬性。  
  
 接收位置屬性的變更會相繼發生。 若解決方案開發人員修改了特定接收位置的屬性值，則新的屬性值會覆寫系統管理員在 BizTalk 管理主控台中為該接收位置設定的全域屬性值。  
  
## <a name="see-also"></a>另請參閱  
 [管理接收位置](../core/managing-receive-locations.md)   
 [成品](../core/artifacts.md)