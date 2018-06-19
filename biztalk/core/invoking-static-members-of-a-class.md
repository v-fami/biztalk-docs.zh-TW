---
title: 叫用類別的靜態成員 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a51171c-8de0-45dd-8659-f674cf27acbe
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2128bf6cb71c773cd31be497765e39b0d7815b4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262270"
---
# <a name="invoking-static-members-of-a-class"></a>叫用類別的靜態成員
根據預設，規則引擎需要您評估 .NET 類別的執行個體以執行叫用 .NET 類別之靜態成員的原則。 您可以修改此行為的值變更**StaticSupport**登錄機碼下的**HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**下表中的值的其中一個。  
  
|StaticSupport 登錄值|規則引擎行為|  
|----------------------------------|--------------------------|  
|0|預設值。 規則引擎遵循 BizTalk Server 2004 模型，其中只有在評估 .NET 類別的執行個體時，才會呼叫靜態方法。|  
|1|不需要物件執行個體。 當評估或執行規則時便會呼叫靜態方法。|  
|2|不需要物件執行個體。 如果所有的參數都是常數，便會在原則轉譯時呼叫靜態方法。 這是一項效能最佳化，因為即使是在多規則的狀況下使用，依然只會呼叫一次靜態方法。 請注意，用來做為動作的靜態方法將不會在轉譯時執行，不過卻可能會執行用來做為參數的靜態方法。|  
  
## <a name="adding-and-changing-the-staticsupport-registry-key"></a>新增和變更 StaticSupport 登錄機碼  
 如果您沒有看到**StaticSupport**登錄機碼下的**HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**，您應該執行下列步驟來加入。  
  
 **若要新增 StaticSupport 登錄機碼**  
  
1.  按一下**啟動**，按一下 **執行**，型別**RegEdit**，然後按一下 **確定**。  
  
2.  展開**HKEY_LOCAL_MACHINE**，依序展開**軟體**，依序展開**Microsoft**，展開**BusinessRules**，然後選取  **3.0**。  
  
3.  在右窗格中，以滑鼠右鍵按一下，指向**新增**，然後按一下  **DWORD 值**。  
  
4.  如**名稱**，型別**StaticSupport**。  
  
 如果**StaticSupport**登錄機碼已經存在，而且您需要變更其值，請執行下列步驟。  
  
> [!IMPORTANT]
>  如果 BizTalk 安裝 64 位元電腦上，則您可以加入**StaticSupport**登錄機碼，使用下列選項之一：  
>   
>  -   您需要查看 HKLM\Software\Wow6432Node\Microsoft\BusinessRules\3.0 底下。 如果此機碼存在，則您可以加入**StaticSupport**這裡。  
> -   另一個選項是將**StaticSupport**中**BTNTsvc [64].exe.config**檔案，任何在這裡的設定會覆寫功能的登錄。  此外，其中也可以將引數，這是慣用選項因為它會隔離預設行為變更至 BizTalk，而登錄設定是全域的作業系統。  
  
 **若要變更 StaticSupport 登錄機碼值**  
  
1.  按一下**啟動**，按一下 **執行**，型別**RegEdit**，然後按一下 **確定**。  
  
2.  展開**HKEY_LOCAL_MACHINE**，依序展開**軟體**，展開**Microsoft**，依序展開**BusinessRules**，然後展開  **3.0**。  
  
3.  按兩下**StaticSupport**登錄機碼，或以滑鼠右鍵按一下它，然後按一下**修改**。