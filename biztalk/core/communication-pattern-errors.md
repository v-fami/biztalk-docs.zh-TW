---
title: 通訊模式錯誤 |Microsoft 文件
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
ms.openlocfilehash: 36677694b8f2d0973c04d942a196d055b696bd5c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232206"
---
# <a name="communication-pattern-errors"></a>通訊模式錯誤
診斷及解決 WCF 通訊模式錯誤的資訊。  

## <a name="fault-messages-are-not-supported-on-one-way-ports"></a>錯誤訊息不支援單向連接埠
  
||錯誤詳細資料|  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|錯誤訊息不支援單向連接埠。 更正服務描述"{0}"連接埠類型 」 {1}"，然後再重新執行精靈|  
  
## <a name="explanation"></a>說明  
 此錯誤表示嘗試從中使用的服務是單向的服務和指定的錯誤。  
  
## <a name="user-action"></a>使用者動作  
 更正服務，請切換至要求-回應從單向通訊模式。 或在程式碼中移除該錯誤。
 
 