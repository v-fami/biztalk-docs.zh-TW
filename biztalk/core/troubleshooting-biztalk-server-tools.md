---
title: 疑難排解 BizTalk Server 工具 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 038a5f5c-d6eb-42db-88d6-70f3deba7a8a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b7aedd8977042d15176781b0595bd5bb225a2fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279766"
---
# <a name="troubleshooting-biztalk-server-tools"></a>BizTalk Server 工具疑難排解
本主題提供集中的位置來存放使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 隨附的工具時經常會遇到之問題的相關資訊。  
  
## <a name="known-issues"></a>已知問題  
  
### <a name="biztalk-server-tools-and-utilities-may-not-function-correctly-on-a-windows-system-that-supports-uac"></a>BizTalk Server 工具和公用程式在支援 UAC 的 Windows 系統上可能無法正常運作  
 **問題**  
  
 當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝在支援使用者帳戶控制 (UAC) 的系統上時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 隨附的工具可能無法順利啟動，或無法正常運作。  
  
 **可能的原因**  
  
 在執行已標示為特定權限等級的應用程式時，如果所需等級高於執行該應用程式的使用者的權限，UAC 會顯示提示，讓您將應用程式權限暫時提升至所需的等級。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 隨附的工具並未啟用正確的旗標來自動要求權限提升，因此，工具會嘗試以執行應用程式的使用者目前的權限等級來執行，但如果需要更高權限，則執行會失敗。  
  
 **解決方式**  
  
 為了解決此問題，請以系統管理權限執行所有 BizTalk Server 工具。 若要以系統管理權限執行一項工具，以滑鼠右鍵按一下應用程式，然後選取**系統管理員身分執行**。  
  
 如需使用者帳戶控制的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=99167](http://go.microsoft.com/fwlink/?LinkId=99167)。  
  
### <a name="sometimes-biztalk-mapper-toolbox-may-appear-empty"></a>BizTalk 對應工具工具箱有時可能會出現空白  
 **問題**  
  
 有時候，當您在 Visual Studio 中開啟對應工具工具箱，看不到任何運算質工具箱中。  
  
 **可能的原因**  
  
 可能是由安裝/解除安裝 Visual Studio 增益集和 （或） patch(es) 可能損毀。  
  
 **解決方式**  
  
 若要解決這個問題：  
  
1.  關閉 Visual Studio 的所有執行的執行個體。  
  
2.  啟動**Visual Studio 命令提示字元**身為系統管理員。  
  
3.  在命令提示字元中，輸入下列命令：  
  
    ```  
    devenv.exe /setup  
    ```