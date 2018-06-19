---
title: 主機 （服務節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Host node [binding file]
ms.assetid: 597522db-0336-43b1-b464-d17cffbf25be
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9c70c23105a8d2f2ebe389b22ddf910b4166994
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246558"
---
# <a name="host-service-node"></a>主控件 (服務節點)
繫結檔案之 [服務] 節點的 [主控件] 節點，說明與該繫結檔案匯出之服務關聯的主控件。  
  
## <a name="nodes-in-the-host-node"></a>主控件節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|名稱|Attribute|xs:string|指定主控件的名稱。|不需要|預設值：空白|  
|NTGroupName|Attribute|xs:string|指定與主控件關聯的 Windows NT 群組名稱。|不需要|預設值：空白|  
|類型|Attribute|xs:int|指定主控件類型為「內含式」或「外掛式」。|Required|預設值：無<br /><br /> 可能的值所述[Microsoft.BizTalk.ExplorerOM.HostType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.hosttype.aspx)列舉型別。|  
|Trusted|Attribute|xs:boolean|指定是否可以信任 BizTalk 主控件進行驗證資訊的收集。|Required|預設值：無<br /><br /> 設定為**true**主機是受信任的否則設為**false**。|