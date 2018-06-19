---
title: 轉換 （InboundTransforms 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Transform node [binding file]
ms.assetid: c1bad23e-78a4-4fd4-95ef-30601393d53c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 705b1b04b8305330ab1d5ff705c5025f24b0685c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279110"
---
# <a name="transform-inboundtransforms-node"></a>轉換 (InboundTransforms 節點)
繫結檔案之 [InboundTransforms] 節點的 [轉換] 節點中，包含隨同該繫結檔案一起匯出之 BizTalk Server 對應的特定相關資訊。  
  
## <a name="nodes-in-the-transform-node"></a>轉換節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|FullName|Attribute|xs:string|指定對應的完整名稱。|不需要|預設值：空白|  
|AssemblyQualifiedName|Attribute|xs:string|指定對應的組件限定名稱。|不需要|預設值：空白|