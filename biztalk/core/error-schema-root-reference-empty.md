---
title: 錯誤-空的結構描述根參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.rootRefEmpty
ms.assetid: 172e6ad8-6118-40db-9451-92808a3a2051
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7217f6f9ea328aff4864cfdf3bee9ea71de3741
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241918"
---
# <a name="error---schema-root-reference-empty"></a>錯誤-空的結構描述根參考
**錯誤碼**  
  
 BEC2005  
  
 **說明**  
  
 **根參考**屬性**結構描述**節點未設定。 當**標準**屬性**結構描述**以外節點設定為值**XML**，您必須設定**根參考**屬性指出哪個子節點**結構描述**要當做此結構描述定義訊息的根節點。  
  
 **使用者動作**  
  
 根據您的結構描述，請將**標準**屬性**結構描述**節點**XML**，或設定**根參考**屬性**結構描述**適當的子節點的節點**結構描述**節點。 這些子節點位於**根參考**屬性下拉式清單。