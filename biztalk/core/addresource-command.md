---
title: "AddResource 命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b09bd8d-5e07-4443-b626-60401a158540
caps.latest.revision: "33"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97d2cb07bd0a05ddd1e79f4048bfe30e51e8d866
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="addresource-command"></a>AddResource 命令
本節主題提供 AddResource 命令相關參數的參考資訊。 這個命令使用的參數會根據您想要加入的成品類型而有所不同。 若要取得成品類型的完整清單，請使用**ListTypes**命令中所述[ListTypes 命令](../core/listtypes-command.md)。  
  
 如需有關加入特定成品類型的輔助說明，請輸入下列命令：  
  
 **BTSTask AddResource/類型：**\<*型別名稱*> **/？**  
  
> [!NOTE]
>  如果您要加入的成品所在的路徑名稱 (包含檔案名稱) 太長，加入成品至應用程式的作業可能會失敗。 路徑不得超過 260 個字元。  
>   
>  加入作業一旦失敗，則作業期間採取的所有動作都將回復，只會保留此命令已加入至全域組件快取中的組件，以及在 Windows 登錄中增修的項目。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [AddResource 命令： BizTalk 組件](../core/addresource-command-biztalk-assembly.md)  
  
-   [AddResource 命令： BizTalk 繫結](../core/addresource-command-biztalk-binding.md)  
  
-   [AddResource 命令：.NET 組件](../core/addresource-command-net-assembly.md)  
  
-   [AddResource 命令： BAM 成品](../core/addresource-command-bam-artifact.md)  
  
-   [AddResource 命令： 憑證](../core/addresource-command-certificate.md)  
  
-   [AddResource 命令： COM 元件](../core/addresource-command-com-component.md)  
  
-   [AddResource 命令： 檔案](../core/addresource-command-file.md)  
  
-   [AddResource 命令： 前置處理指令碼](../core/addresource-command-preprocessing-script.md)  
  
-   [AddResource 命令： 後置處理指令碼](../core/addresource-command-postprocessing-script.md)  
  
-   [AddResource 命令： 原則](../core/addresource-command-policy.md)  
  
-   [AddResource 命令： 虛擬目錄](../core/addresource-command-virtual-directory.md)