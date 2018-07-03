---
title: 如何套用和移除追蹤設定檔 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting, tracking profiles
- tracking profiles, testing
- tracking profiles, deleting
- testing, tracking profiles
ms.assetid: 77cef14b-c390-4da7-a383-b3abe414a168
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffc3b321647a5861a4b4b3d24251f1ecf013ee09
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985023"
---
# <a name="how-to-apply-and-remove-a-tracking-profile"></a>如何套用和移除追蹤設定檔
在建立或修改追蹤設定檔之後，下一個步驟就是將它套用到測試資料庫，並透過整合測試驗證結果。 您可從追蹤設定檔編輯器 (TPE) 本身或使用命令列套用追蹤設定檔。  
  
## <a name="prerequisites"></a>必要條件  
 您之前已建立並儲存到硬碟的追蹤設定檔。  
  
### <a name="to-apply-the-tracking-profile-from-within-the-tpe"></a>從 TPE 套用追蹤設定檔  
  
1. 按一下 **開始**，指向**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**Tracking Profile Editor**。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。 若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。  
  
2. 在 **檔案**功能表上，按一下**開啟**。 瀏覽至硬碟上正確的 .btt 檔。 按一下 **開啟**載入它。  
  
3. 在上**工具**功能表上，按一下**套用追蹤設定檔**.btt 檔套用至管理資料庫，您已將來自**設定管理資料庫**功能表項目**工具**功能表。 透過整合測試驗證結果。  
  
4. 請通知您組織中負責部署的人員，追蹤設定檔測試正常並且已可供部署。  
  
### <a name="to-apply-the-tracking-profile-from-the-command-line"></a>從命令列套用追蹤設定檔  
  
-   在命令提示字元中執行位於 \Tracking 資料夾中的 bttdeploy.exe 工具，如下所示：  
  
    ```  
    bttdeploy.exe <profile name>.btt  
    ```  
  
> [!NOTE]
>  您必須具有 BizTalk 系統管理員權限才可使用此工具。  
  
> [!NOTE]
>  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。 若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。  
  
> [!IMPORTANT]
>  在部署期間，bttdeploy 會驗證追蹤設定檔中所包含的組件版本，並與已部署之組件的版本進行比對。 如果該組件目前尚未部署，bttdeploy 就會失敗。  
  
> [!IMPORTANT]
>  從命令列套用追蹤設定檔時，bttdeploy 會將設定檔套用到您在執行組態精靈時所指定的 BizTalk 管理資料庫。 如果您在追蹤設定檔編輯器選項「設定管理資料庫」中指定不同的資料庫設定，則便會使用該設定。 如果您指定管理伺服器和資料庫做為 bttdeploy 命令列選項的一部分，則該命令列選項會覆寫所有其他部分。 如需使用 bttdeploy 的詳細資訊，請參閱 <<c0> [ 追蹤設定檔部署公用程式](../core/tracking-profile-deployment-utility.md)。  
  
### <a name="to-remove-a-tracking-profile"></a>移除追蹤設定檔  
  
1. 按一下 **開始**，指向**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**Tracking Profile Editor**。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。 若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。  
  
2. 在 **檔案**功能表上，按一下**開啟**。 瀏覽至硬碟上正確的 .btt 檔。 按一下 **開啟**載入它。  
  
3. 在 [**工具**] 功能表中，按一下**移除追蹤設定檔**移除 BizTalk 管理資料庫中的.btt 檔案為基礎的追蹤設定檔。  
  
## <a name="see-also"></a>另請參閱  
 [建立追蹤設定檔](../core/creating-tracking-profiles.md)