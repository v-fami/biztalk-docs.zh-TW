---
title: 迴圈包含分葉節點。 它只可以包含其他迴圈或區段 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a0ee5e6-519d-4c95-8681-de5a37741d56
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d03349389fb108d434cce67afc5be13fd2a3d513
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278830"
---
# <a name="the-loop-contains-a-leaf-node-it-can-only-contain-other-loops-or-segments"></a>迴圈包含分葉節點。 它只能包含其他迴圈或區段
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|SchemaCode125ELoopContainsLeafNode|  
|訊息文字|迴圈包含分葉節點。 它只能包含其他迴圈或區段|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送的交換，因為文件結構描述不符合交換。 在此情況下，由於迴圈包含 childless 分葉節點，而指定的結構描述的迴圈可能只會包含其他迴圈或區段。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，具有寄件者的交換修正迴圈，使其不包含分葉節點，然後再重新傳送交換。