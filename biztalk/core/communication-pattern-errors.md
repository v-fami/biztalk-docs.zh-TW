---
title: 通訊模式錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06656073-9bae-4d6f-98ae-2714a72ee79c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef9f7f4419d6c95b9b11343f395ab8e3d17c7c34
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021081"
---
# <a name="communication-pattern-errors"></a>通訊模式錯誤
診斷及解決 WCF 通訊模式錯誤的資訊。  

## <a name="fault-messages-are-not-supported-on-one-way-ports"></a>單向連接埠上不支援將錯誤訊息
  
|                 |                                                       錯誤詳細資料                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                     |
| 產品版本 |                                [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                 |
|    事件識別碼     |                                                             0                                                             |
|  事件來源   |                                                             0                                                             |
|    元件    |                                                             0                                                             |
|  符號名稱  |                                                             0                                                             |
|  訊息文字   | 單向連接埠上不支援將錯誤訊息。 更正服務描述"{0}「 連接埠類型 」{1}"，然後重新執行精靈 |
  
## <a name="explanation"></a>說明  
 此錯誤表示嘗試取用的服務是單向服務，而且具有指定的錯誤。  
  
## <a name="user-action"></a>使用者動作  
 請更正服務藉由切換至要求-回應從單向通訊模式。 或在程式碼中移除錯誤。
 
 