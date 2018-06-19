---
title: SWIFT 的標頭和結尾結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- trailer schemas
- schemas, headers
- schemas, trailers
- header schemas
ms.assetid: 82cd33d4-6bbb-4124-9506-fd35b5dca8a4
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8f3cb45e14a7c7e900fc26a4cbc8fcfb5d7b66e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214574"
---
# <a name="swift-header-and-trailer-schemas"></a>SWIFT 的標頭和結尾結構描述
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]提供 SWIFT 標頭和結尾結構描述。 A4SWIFT 已經已納入這些各種 FIN 訊息交換的結構描述。 如果您想要建立自訂 SWIFT FIN 格式樣式訊息類型 （例如，N98 訊息），您可以在標頭和結尾結構描述併入您自己的格式。  
  
 SWIFT 的標頭結構描述 (SWIFT Header.xsd) 包含下列格式：  
  
-   基本的標頭  
  
-   應用程式標頭 （選擇輸入或輸出）  
  
-   使用者標頭  
  
-   文字區塊的起始分隔符號  
  
 基本的標頭包含屬於訊息來源之相關資訊。 應用程式標頭包含訊息類型和訊息的目的地的相關資訊。 SWIFT 的解譯器，接收管線中的訊息類型解析根據適當的應用程式標頭中欄位的內容。 使用者標頭是選擇性的並包含特殊的處理指示。  
  
> [!NOTE]
>  少數的訊息類型會顯示變數的格式欄位 119 使用者標頭中的內容為基礎。 這些是在 A4SWIFT 的 「 雙重訊息類型 」。 A4SWIFT 解譯器使用應用程式中的標頭搭配 119 欄位的內容中的訊息類型，選取適當的結構描述的訊息執行個體。  
  
 *SWIFT 使用者手冊*，這是 SWIFT FIN 服務文件的部分描述所有這些標頭。  
  
 文字區塊的開頭是"{4: 」 後面接著歸位字元和換行字元。 需要文字區塊的開頭。  
  
 為了要考慮處理 （剖析及驗證） 的交換包含只 SWIFT 區塊 4，交換結構描述中的所有標頭和結尾區塊會標示為選擇性。 這偏離 SWIFT FIN 規格，其中基本的標頭區塊 1 和 2 應用程式標頭區塊是強制性。 這可讓您使用交換的結構描述來處理不要求標頭的訊息。 例如，如果您接受透過 FileAct 收到的訊息，批次標頭可能包含訊息，以及一般的訊息類型的來源。  
  
 執行階段結構描述 DLL 也包含標頭結構描述。 A4SWIFT 安裝部署執行階段結構描述 DLL 和 A4SWIFT 屬性結構描述。 如果您需要使用您自己的標頭，以便進行處理，您可以定義和部署自訂標頭結構描述，並將升級訊息解析為適當的屬性。 如果您這樣做，您也必須指定新的標頭 SWIFT 解譯器 (DASM)。 自訂標頭結構描述不應該有相同的文件類型為 SWIFT 標頭結構描述該 A4SWIFT 安裝已部署在執行階段結構描述 DLL 中。 請務必變更結構描述命名空間或根節點名稱，或兩者。  
  
 SWIFT 結尾結構描述 (**SWIFT Trailer.xsd**) 包含下列格式：  
  
-   文字區塊的結尾分隔字元  
  
-   使用者結尾 （使用者和系統資訊）  
  
-   系統結尾  
  
 文字區塊的結束分隔符號是"-"}。 結尾區塊的開頭"{5:"。 結尾區塊的內容會包含使用者資訊 （總和檢查碼、 訊息驗證，專屬的驗證，等等） 和系統資訊 （延遲的訊息，訊息參考，可能重複的訊息，以及等等）。 SWIFT 所加入的結尾也提供第三個區塊，以分隔"{S"。 *SWIFT 使用者手冊*，在 [尋找服務描述]，詳細說明區塊 5 的內容。 A4SWIFT 不會驗證 s 區塊的內容  
  
 實際的 FIN 介面或 SWIFT 網路將附加至結尾。 如果訊息包含結尾 A4SWIFT 接收訊息時，A4SWIFT 會有訊息結尾。 如果訊息沒有結尾 A4SWIFT 接收訊息時，A4SWIFT 就不會引發錯誤。 做為標頭與結尾的項目，包括區塊本身，均 A4SWIFT 的選擇性參數。  
  
## <a name="see-also"></a>另請參閱  
 [使用結構描述](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)