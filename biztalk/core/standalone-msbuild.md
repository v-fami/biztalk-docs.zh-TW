---
title: 獨立式 MSBUILD |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 21aa3693-3788-4874-b506-6f4584fb4fd5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcee1d06bf57eb2ea98c214501c2499f0ce83d95
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007695"
---
# <a name="standalone-msbuild"></a>獨立式 MSBUILD
**專案建置**元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓您建立 BizTalk Server solutions 不含[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。 若要安裝**專案建置**您在伺服器上，選取元件**專案建置元件**選項**其他軟體類別**在安裝期間。 您應該取消選取**開發者工具與 SDK**安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]沒有的電腦上[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
 如需 MSBUILD 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567)。  
  
## <a name="to-build-a-biztalk-project"></a>建置 BizTalk 專案  
  
1.  按一下 **[開始]**，並按一下 **[執行]**。  
  
2.  型別**cmd**，然後按 ENTER。  
  
3.  切換至專案目錄，然後執行 MSBUILD 命令以建置 BizTalk 方案。  
  
    ```  
    msbuild unittesttest.sln /p:Configuration=Debug  
    ```  
  
    > [!TIP]
    >  您可能需要設定 PATH 環境變數，以指向資料夾 msbuild.exe 所在 (\<*windows 安裝目錄*\>\Microsoft.NET\Framework\v4)。