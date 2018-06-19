---
title: EDI 交易集訊息結構元素 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: caea8408-c09c-4525-a9c9-18abe4432594
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d49288e9a311c9766e61fe985b9e279a8660f4ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239182"
---
# <a name="edi-transaction-set-message-structural-element"></a>EDI 交易集訊息結構元素
交易集 (X12 編碼) 或訊息 (EDIFACT 編碼) 包含組成訊息資料的區段。 交易集由標頭、資料區段集合和結尾組成。 交易處理時所需要的詳細資料都會包含在交易集中。  
  
 交易集的開頭必須是 ST 交易集標頭 (X12) 或 UNH 訊息標頭 (EDIFACT)。 它的結尾必須是 SE 交易集結尾 (X12) 或 UNT 訊息結尾 (EDIFACT)。 結尾會提供資料區段計數，這些區段包括標頭和結尾區段。  
  
 交易集可以包含一或多個迴圈，以便在需要重複相關區段的集合時使用。