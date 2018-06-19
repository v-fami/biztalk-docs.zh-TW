---
title: EDI 資料項目結構元素 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 775e8b87-b952-46d2-a506-5174d216a9aa
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 600edb30ff157a520ac67eebce58428a62e27c8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239470"
---
# <a name="edi-data-element-structural-element"></a>EDI 資料項目結構元素
這種資料元素是訊息中的主要資料單位。 資料元素分隔的資料元素分隔符號，也就是星號，根據預設，對於 X12 和 EDIFACT 的預設值加上加號。 資料元素的選用性分為強制性、選用性或條件性。  
  
 資料元素可以是簡單或複合。 簡單資料元素為數字形式，屬於最低層的資料。 複合資料元素為的子元素，這是由元件分隔符號隔開的簡單資料元素的串連。 根據預設，元件分隔符號是 X12 和 EDIFACT 的冒號。  
  
 對於 EDIFACT 編碼訊息，如果要透過 EDI 傳送的資料需要傳送任何字元，定義用來做為分隔符號，您需要使用釋放字元表示接的字元不是為分隔符號，而是資料的一部分。 預設的釋放字元為問號 (?)。  
  
> [!NOTE]
>  X12 不支援釋放字元。 如果 X12 編碼交換資料中出現分隔符號，無論在接收端或是傳送端，該交換都會遭到擱置。