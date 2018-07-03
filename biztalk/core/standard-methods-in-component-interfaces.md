---
title: 元件介面中的標準方法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- component interfaces, standard methods
- methods, viewing
- methods, component interfaces
- methods, changing
ms.assetid: 2273d946-3fc8-4b2d-a6a1-9e4f0da74d5b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eecb56f262a56e6567b44b146c631542cb1ceda6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994823"
---
# <a name="standard-methods-in-component-interfaces"></a>元件介面中的標準方法
元件介面的標準方法如下所示：  
  
- `Create`  
  
- `Find`  
  
- `Get`  
  
- `Save`  
  
  只有基礎元件中的那些方法才能夠使用。 例如，假設基礎元件不包含 `Add` 功能，就無法使用 `Create`。  
  
## <a name="viewing-or-changing-available-methods"></a>檢視或變更可用方法  
  
#### <a name="to-view-or-change-available-methods"></a>檢視或變更可用方法  
  
1.  開啟元件介面**屬性** 對話方塊。  
  
     ![](../core/media/psadapter-46-ps-properties.gif "PSAdapter_46_PS_Properties")  
  
2.  按一下 [**標準方法**] 索引標籤。  
  
3.  選取需要的方法，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [如何建立元件介面](../core/how-to-create-component-interfaces.md)   
 [附錄 C：使用元件介面](../core/appendix-c-using-component-interfaces.md)