---
title: BTAD_SilentMode |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BTAD_SilentMode [environment variable], about BTAS_SilentMode
- BTAD_SilentMode [environment variable]
- BTAD_SilentMode [environment variable], warnings
ms.assetid: 271835cf-1587-44c5-b5af-b4df4e981ab4
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31715835c98d2f60a3b5f1c18251571ea57641d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231326"
---
# <a name="btadsilentmode"></a>BTAD_SilentMode
BTAD_SilentMode 指定採用無訊息模式執行指令碼的選項。  
  
## <a name="remarks"></a>備註  
 當您指定無訊息模式的選項時，BTS Installer 便會將其值存放在 BTAD_SilentMode 變數中。  
  
 BTAD_SilentMode 的預設值為 2，這會指定要在無訊息模式中執行指令碼。 下表描述 BTAD_SilentMode 的可能值。  
  
> [!CAUTION]
>  如果您從指令碼中啟動 BizTalk Server 使用者介面，其強制回應對話方塊可能無法顯示或者沒有焦點，要加以檢視或關閉就變得很困難。 當強制回應對話方塊開啟時，可能會讓 BizTalk 資料庫處在鎖定狀態而無法存取。 因此，實際執行系統上的所有指令碼都應該在無訊息模式下執行。  
  
|Value|描述|  
|-----------|-----------------|  
|0|不會變更使用者介面 (UI) 層級。|  
|1|使用預設 UI 層級。|  
|2|執行無訊息安裝 (預設)。|  
|3|提供簡單的進度和錯誤處理。|  
|4|提供設計的 UI，並將精靈隱藏起來。|  
|0x80|與上述任一個值合併使用時，如果指令碼執行成功或是發生錯誤，Windows Installer 將會顯示強制回應對話方塊。 如果使用者取消作業，則不會顯示任何對話方塊。|  
|0x40|如果與 3 這個值合併使用，Windows Installer 將顯示進度對話方塊，但不會顯示任何強制回應對話方塊或錯誤對話方塊。|  
|0x20|如果與 3 這個值合併使用，Windows Installer 將顯示進度對話方塊，但不會顯示任何強制回應對話方塊或錯誤對話方塊。|  
|0x100|如果與 3 這個值合併使用，Windows Installer 將顯示進度對話方塊，但不會顯示任何強制回應對話方塊或錯誤對話方塊。|  
  
## <a name="see-also"></a>另請參閱  
 [前置和後置處理指令碼環境變數](../core/pre-and-post-processing-script-environment-variables.md)   
 [環境變數如何指示部署狀態](../core/how-environment-variables-indicate-deployment-state.md)