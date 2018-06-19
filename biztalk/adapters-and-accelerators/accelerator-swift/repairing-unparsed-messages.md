---
title: 修復未剖析的訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unparsed messages
- repairing messages, unparsed messages
- messages, unparsed messages
ms.assetid: cc061243-3539-4407-a096-71a3feded1c5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de427afc854bf782f69a8c0428a874c61ffb5c4f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214542"
---
# <a name="repairing-unparsed-messages"></a>修復未剖析的訊息
如果[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]解譯器無法剖析訊息，您可以修復該訊息。 請在[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單內[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]MRSR 站台。 不過，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]處理該訊息以不同的方式從修復的訊息 XML 或 BRE 驗證失敗。  
  
 如果訊息或批次失敗的剖析，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]將其標示為[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed = True，以剖析錯誤計數大於 0。 訊息內文會保留在一般檔案格式，抓住中的 XML 包裝函式。 如果修復規則設定為 允許處理的剖析失敗，訊息會傳送未剖析的收件匣處理使用未剖析的表單。  
  
 不會有一個未剖析的收件匣的所有使用者和所有的部門，因為[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]可能沒有任何訊息的相關資料的存取權以外原始接收位置。 如此一來，若要修復未剖析的訊息，使用者必須具有 「 修復 」 功能，而且必須在所有部門中的修復角色相關聯。  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]顯示未剖析的訊息中的文字區域的 Unparsed[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。 若要更正剖析問題，您可能輸入，或刪除視字元。 提交之後，訊息是擷取自 XML 包裝函式，並重新提交透過 SWIFT 接收管線。 如果剖析成功，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]處理訊息，如同任何其他訊息。  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]不會處理您透過完整的修復工作流程已修正未剖析的訊息。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]傳送出去未驗證和未經核准。 當您登入修復的未剖析的訊息，然後提交，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]不呼叫 BRE 驗證或檢查部門，但直接至傳送管線傳送訊息。 如果該管線無法處理訊息，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]將它傳送到修復程序。  
  
 此程序可讓您更正來自另一個系統的格式錯誤訊息。 不過，您應謹慎小心修正剖析問題時。 當[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]處理未剖析的訊息，不會驗證訊息。 未剖析的修復未定義為角色，讓任何人都可以執行此程序。 因為未剖析的訊息不屬於任何部門，存取它們所提供的唯一安全性就會是未剖析的收件匣上的 Acl。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]也不會保留原始接收位置未剖析的訊息的訊息內容屬性。  
  
 您可以撰寫自訂的驗證，以修復未剖析的訊息上執行。 您也可以撰寫修復的未剖析的訊息傳送至原始檔管線訂用帳戶。  
  
 用於剖析訊息修復機制，您需要將 EnvelopeUnparsedMessage.xsd 結構描述加入至包含訊息結構描述的組件。 如需詳細資訊，請參閱[部署 A4SWIFT 結構描述](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md)。