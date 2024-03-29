---
title: 如何變更前置或後置處理指令碼的目的地位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scripts, file locations
- scripts, modifying
- managing [scripts], modifying
- managing [scripts], file locations
ms.assetid: 4a4fdaef-099f-4c29-9815-12404c7a2212
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f6d1a7ec9f661a86ff028b1ec364bbd656cbb2b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005287"
---
# <a name="how-to-change-the-destination-location-of-a-pre--or-post-processing-script"></a>如何變更前置或後置處理指令碼的目的地位置
本主題描述如何使用 [BizTalk Server 管理主控台] 來變更前置或後置處理指令碼的目的地位置。 這是在安裝應用程式時便會將指令碼複製到其中的位置。 在將應用程式部署到不同的環境時，您就可能需要變更目的地位置。  
  
> [!IMPORTANT]
>  請確定為解除安裝應用程式時執行的指令碼提供目的地位置。 如果沒有提供位置，就不會將指令碼複製到本機檔案系統，因此不會在解除安裝時執行。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-modify-the-deployment-properties-of-a-pre--or-post-processing-script"></a>若要修改前置或後置處理指令碼的部署屬性  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 展開包含要修改的指令碼的 BizTalk 群組，然後再展開 應用程式包含指令碼。  
  
3. 按一下 **資源**資料夾中，以滑鼠右鍵按一下指令碼，然後**修改**。  
  
4. 在 **目的地位置**，輸入目的地位置，包括檔案名稱的完整路徑，然後按一下**確定**。 (您可以在路徑中使用 %BTAD_InstallDir% 環境變數來指定應用程式安裝資料夾)。  
  
## <a name="see-also"></a>另請參閱  
 [管理前置和後置處理指令碼](../core/managing-pre-and-post-processing-scripts.md)