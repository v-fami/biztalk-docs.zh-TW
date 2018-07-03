---
title: 叫用類別的靜態成員 |Microsoft Docs
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
ms.openlocfilehash: f3cb6a673fcf7fb363de678eceefd62802a063ca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022076"
---
# <a name="invoking-static-members-of-a-class"></a>叫用類別的靜態成員
根據預設，規則引擎需要您評估 .NET 類別的執行個體以執行叫用 .NET 類別之靜態成員的原則。 您可以修改此行為變更的值**StaticSupport**登錄機碼底下**HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**其中一個下表中的值。  
  
|StaticSupport 登錄值|規則引擎行為|  
|----------------------------------|--------------------------|  
|0|預設值。 規則引擎遵循 BizTalk Server 2004 模型，其中只有在評估 .NET 類別的執行個體時，才會呼叫靜態方法。|  
|@shouldalert|不需要物件執行個體。 當評估或執行規則時便會呼叫靜態方法。|  
|2|不需要物件執行個體。 如果所有的參數都是常數，便會在原則轉譯時呼叫靜態方法。 這是一項效能最佳化，因為即使是在多規則的狀況下使用，依然只會呼叫一次靜態方法。 請注意，用來做為動作的靜態方法將不會在轉譯時執行，不過卻可能會執行用來做為參數的靜態方法。|  
  
## <a name="adding-and-changing-the-staticsupport-registry-key"></a>新增和變更 StaticSupport 登錄機碼  
 如果您看不見**StaticSupport**登錄機碼底下**HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**，您應該執行下列步驟來新增。  
  
 **若要新增 StaticSupport 登錄機碼**  
  
1. 按一下 **開始**，按一下**執行**，型別**RegEdit**，然後按一下 **確定**。  
  
2. 依序展開**HKEY_LOCAL_MACHINE**，展開**軟體**，展開**Microsoft**，展開**BusinessRules**，然後選取  **3.0**。  
  
3. 在右窗格中，以滑鼠右鍵按一下，指向**的新**，然後按一下**DWORD 值**。  
  
4. 針對**名稱**，型別**StaticSupport**。  
  
   如果**StaticSupport**登錄機碼已經存在，而且您需要變更其值，請執行下列步驟。  
  
> [!IMPORTANT]
>  如果 BizTalk 安裝在 64 位元電腦上，則您可以加入**StaticSupport**登錄機碼使用下列其中一個選項：  
> 
> - 您需要查看 HKLM\Software\Wow6432Node\Microsoft\BusinessRules\3.0 底下。 如果此機碼存在，則您可以加入**StaticSupport**這裡。  
>   -   另一個選項是將放**StaticSupport**中**BTNTsvc [64].exe.config**檔案，因為此處的任何設定覆寫功能的登錄。  此外，其中也可以將引數，這是慣用選項因為它會隔離的預設行為變更至 BizTalk，而登錄設定是全域的作業系統。  
  
 **若要變更 StaticSupport 登錄機碼值**  
  
1.  按一下 **開始**，按一下**執行**，型別**RegEdit**，然後按一下 **確定**。  
  
2.  依序展開**HKEY_LOCAL_MACHINE**，展開**軟體**，展開**Microsoft**，展開**BusinessRules**，然後展開  **3.0**。  
  
3.  按兩下**StaticSupport**登錄機碼，或以滑鼠右鍵按一下它，然後按一下**修改**。