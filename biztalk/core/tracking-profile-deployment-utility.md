---
title: "追蹤設定檔部署公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d631b7c-a40f-4cee-88a4-3d932ab7fde0
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c4d261069b83741413e255a3f8bacd6dd9260d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tracking-profile-deployment-utility"></a>追蹤設定檔部署公用程式
開發人員使用 bttdeploy 公用程式，對 BAM 基礎結構套用或移除追蹤設定檔。 使用 bttdeploy 公用程式的效用等同於在「追蹤設定檔編輯器」(TPE) 中按一下 [套用追蹤設定檔] 功能表選項。  
  
> [!NOTE]
>  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
 **使用方式**  
  
 **bttdeploy.exe [選項] 的檔案名稱**  
  
|選項|Description|  
|------------|-----------------|  
|/h 或 /?|選擇項：顯示 bttdeploy 的語法摘要。|  
|/mgdb \<name> [，連接埠] >\\< 資料庫名稱\>|選擇項：指定要套用設定檔的管理伺服器、連接埠及資料庫名稱。 **注意：**使用這個參數時，是選擇性的連接埠。|  
|/remove|選擇項：指定要從 BAM 資料庫移除追蹤設定檔。|  
|filename|要套用或移除的追蹤設定檔檔案名稱。|  
  
## <a name="see-also"></a>另請參閱  
 [追蹤設定檔編輯器](../core/tracking-profile-editor.md)   
 [如何移除被遺棄的追蹤設定檔](../core/how-to-remove-orphaned-tracking-profiles.md)