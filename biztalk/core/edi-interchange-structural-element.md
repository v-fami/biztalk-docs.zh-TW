---
title: EDI 交換結構元素 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03f47ae2-fa0f-4d88-a700-85f3d515d2d0
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc07ae40a3665b47b446b61e24954ca9c588a6a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239526"
---
# <a name="edi-interchange-structural-element"></a>EDI 交換結構元素
此交換是 EDI 訊息的最高層結構元素。 它包含由兩個夥伴交換之一或多個群組的集合。 交換的目的地必須是單一交易夥伴。 交換可能會包含一或多種類型的交易集/訊息。  
  
 進行交換時，交換本身以及其中的群組和交易集/訊息是由標頭定義。 區段、資料元素和子元素以分隔符號來區隔。 雖然每個分隔符號都具有預設值，但是可能會針對合作對象定義成不同的字元。 在 EDIFACT 交換中，選取做為交換中之分隔符號的字元是在單獨的 UNA 交換標頭中定義。 在 X12 交換中，分隔符號是在 ISA 交換標頭中定義。 請注意，在 X12 中，資料元素分隔符號是位於第四個字元位置的字元，而資料區段結束字元是位於最後一個字元位置的字元。 其他 X12 分隔符號和所有的 EDIFACT 分隔符號由所定義的欄位，例如 X12 ISA16 欄位，EDIFACT 資料項目分隔符號 UNA2 欄位的元件分隔符號。  
  
 此交換包含定義 EDI 訊息的信封。 此信封必須以交換標頭 (X12 中的 ISA 或 EDIFACT 中的 UNA/UNB) 為開頭，而且它必須以交換結尾 (IEA/UNZ) 為結尾。 交換標頭包含定義傳送者和接收者的元素、日期與時間、版本號碼、與標頭和結尾相符的控制編號，以及其他資訊。  
  
 ISA12 和 GS8 欄位 (適用於 X12 交換) 以及 UNH2 欄位 (適用於 EDIFACT 交換) 包含結構描述探索所需的版本資訊。  
  
 交換結尾具有指出交換內部群組數目的元素。  
  
> [!NOTE]
>  功能安全性標頭、功能確保標頭、功能安全性值區段和功能安全性結尾區段已超出 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI 和 AS2 的範圍。 如果您收到含有這些區段的交換，系統就會擱置此作業並顯示錯誤記錄，表示這些是無法識別的區段。