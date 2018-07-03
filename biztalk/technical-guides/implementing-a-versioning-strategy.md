---
title: 實作版本控制策略 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0a3c7af6-6277-4667-8f14-e6d1cb9e99d4
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8990fb3d65b29609738ed398829a438478eeabb3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015039"
---
# <a name="implementing-a-versioning-strategy"></a>實作版本控制策略
版本控制是指更新成品的實作並遞增其版本號碼。  
  
## <a name="general-versioning-issues"></a>一般版本控制的問題  
 BizTalk 應用程式版本可能會產生問題，當您需要執行兩個版本的 BizTalk 方案的並行，或如果您無法排程部署的新版本的 BizTalk 應用程式停機時間。 如果您不需要執行兩個版本同時 （例如，如果您不有任何長時間執行的協調流程） 的解決方案，它是完全解除部署舊版本和部署新的版本與版本控制策略 （沒有組件版本控制）。 這會是可能的版本控制策略，不過我們還是建議遞增檔案版本號碼 （若要讓您知道哪一個版本部署在 BizTalk server 上）。 如需有關如何更新部署的應用程式的詳細資訊，請參閱[檢查清單： 更新組件](../technical-guides/checklist-updating-an-assembly.md)。  
  
 如果您需要支援長時間執行的協調流程，和/或您需要執行任何 BizTalk 應用程式停機時間的 BizTalk 應用程式部署，然後紮實的 BizTalk 版本控制策略需要實作並且身體力行端對端的不同版本控制案例。 這包括.NET 組件版本控制和所有的 BizTalk 成品的版本控制。 這包括結構描述、 對應、 管線、 管線元件、 協調流程、 自訂配接器、 自訂類別中呼叫的協調流程、 對應、 商務規則與 BAM。 如需詳細的並存版本控制的詳細資訊，請參閱[更新使用並排顯示版本控制](../technical-guides/updating-using-side-by-side-versioning.md)。  
  
## <a name="versioning-an-assembly"></a>組件的版本控制  
 當您更新組件時，您會有下列選擇：  
  
- 選擇的固定的組件的版本特定的傳遞標並遞增只有檔案版本號碼。  
  
- 在開發的過程中，遞增檔案版本和組件版本。  
  
  這些方法會在下表比較：  
  
|**固定的組件版本，動態檔案版本**|**動態組件版本，固定或動態檔案版本**|  
|------------------------------------------------------|-----------------------------------------------------------------|  
|組件版本號碼 = 固定編號<br /><br /> 檔案版本號碼 = 組建編號|組件版本號碼 = 組建編號<br /><br /> 檔案版本號碼 = 組建編號|  
|如果多個組件會安裝 BizTalk Server 執行階段可能會挑選錯誤的組件版本。|BizTalk Server 一律執行最新版的組件，即使已安裝多個組件。|  
|任何時候都只能部署一種解決方案版本。|（雖然可能會發生衝突的解決方案，例如結構描述定義的其他層面），可以並存部署解決方案的不同版本。|  
|BizTalk 主控件需要重新啟動，才能強制載入更新的組件。|強制載入新的組件的 BizTalk Server。|  
|建立新的部署作業時比較不費力，因為參考組件版本號碼的檔案 (例如繫結檔案與追蹤設定檔) 不需要加以編輯。|部署作業比較費力，因為參考組件版本號碼的檔案需要保持更新為最新版本。|  
  
 您可以選擇使用固定的組件版本與動態檔案版本方法，如果您是建立一個系統原型，或是開發任何其他類型的專案，將不會釋放。 如果您不打算將應用程式傳遞給一般使用者，可以將組件版本固定下來，並遞增檔案版本號碼來簡化部署作業並降低相依性被破壞的可能性。 針對版本追蹤，請務必記得為每個組建遞增檔案版本號碼。  
  
 如果您所建立的專案將會傳遞給一般使用者，應該要考慮遞增組件版本，並且選擇性地將有意義的檔案版本號碼儲存起來。 雖然這個方法在修改組建編號以及與其關聯之相依性時會增加額外的工作，卻能夠確保您的組件已更新至最新的版本。 透過使用自動化的部署指令碼，您可以降低版本管理的影響。 若要檢視部署範例，請參閱[應用程式部署 （BizTalk Server Samples 資料夾）](http://go.microsoft.com/fwlink/?LinkId=155134) (<http://go.microsoft.com/fwlink/?LinkId=155134>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
> [!NOTE]  
>  您應該選擇的版本控制機制，可確保適當的檔案傳遞，並簡化維護和增強功能。  
  
 如需版本控制問題的詳細資訊，請參閱[BizTalk Server 專案版本管理](http://go.microsoft.com/fwlink/?LinkID=154209)(<http://go.microsoft.com/fwlink/?LinkID=154209>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。