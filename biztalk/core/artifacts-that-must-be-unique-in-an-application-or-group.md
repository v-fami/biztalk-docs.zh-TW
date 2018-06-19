---
title: 中的應用程式或群組必須是唯一的成品 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- groups, artifacts
- artifacts, requirements
- applications, artifacts
ms.assetid: a758cd74-a962-4e75-aea2-47752ab72a64
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfe9ff033621ed491b7f1deae9e3f2e467e54f83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230382"
---
# <a name="artifacts-that-must-be-unique-in-an-application-or-group"></a>在應用程式或群組中必須是唯一的成品
BizTalk 群組或應用程式中某些類型的成品必須是唯一的，如下所示：  
  
-   BizTalk 組件和非 BizTalk .NET 組件在此群組中都必須有唯一的完整名稱。 完整名稱是由檔案名稱、公開金鑰語彙基元、文化特性和版本所組成。  
  
-   規則和原則在此群組中都必須有唯一的名稱和版本號碼。  
  
-   傳送埠、傳送埠群組、接收埠和接收位置在此群組中必須有唯一的名稱。  
  
-   網站在此群組中必須有唯一的虛擬目錄名稱。  
  
-   BAM 資源在此群組中必須有唯一的檔案名稱。  
  
-   憑證在此群組中必須有唯一的憑證指紋。  
  
-   COM 元件在此群組中必須有唯一的檔案名稱。  
  
-   以檔案為基礎的成品 (如指令碼和其他一般檔案) 在應用程式中必須有唯一的檔案名稱 (而不是在此群組中)。  
  
 如果某成品已經存在於應用程式中，而且其類型在應用程式中必須是唯一的，您可以指定覆寫選項來匯入或新增此成品至應用程式。 如果此成品已經存在於此群組的另一個應用程式中，而且其類型在此群組中必須是唯一的，您將無法新增或匯入它。  
  
 如果您需要使用某個應用程式中的成品，而且它已經存在於此群組的另一個應用程式中，您可以建立一個參考，使其參考包含此成品的應用程式。 如需詳細資訊，請參閱[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。  
  
> [!NOTE]
>  您可以檢視大部分成品類型的完整名稱的應用程式中使用 BTSTask 的 ListApp 命令中所述[ListApp 命令](../core/listapp-command.md)。  
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md)