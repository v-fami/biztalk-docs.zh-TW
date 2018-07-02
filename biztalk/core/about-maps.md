---
title: 關於對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- file types, maps
- BizTalk Mapper
- maps, file type
- maps, about maps
- BizTalk Mapper, about BizTalk Mapper
- maps
ms.assetid: 512ef2b7-3d01-4fcf-bb38-de68ec608b07
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd27793be4f1b1d9fd2b404f9a2a3a678b7622b2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966279"
---
# <a name="about-maps"></a>關於對應
您可使用 [BizTalk 對應工具]，利用連結和運算質定義輸入和輸出結構描述之間的關係。 連結定義記錄或欄位的直接資料複本。 連結可以直接連接項目到另一個結構描述，也可以建立與運算質的連接。 運算質可執行複雜的資料操作，例如：  
  
- 在來源結構描述中新增兩個欄位的值，並將結果複製到目的結構描述。  
  
- 將字元轉換為其 ASCII 格式。  
  
- 傳回重複記錄中欄位的平均值，並將結果複製到目的結構描述中的欄位。  
  
  [BizTalk 對應工具] 會將對應儲存到副檔名為 .btm 的檔案中。 檔案會儲存對應的設計資訊，例如代表運算質之圖示的位置、結構描述項目與運算質之間的連結，以及對應的其他資訊。 建置或編譯對應時，[BizTalk 對應工具] 會將對應的相關資訊轉換為對應的「可延伸樣式表語言轉換」(XSLT) 樣式表。  
  
> [!NOTE]
>  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 編譯器在單一專案中，所有字串總大小的限制為 16 MB。 在編譯 BizTalk 專案時，編譯器會序列化結構描述、對應和協調流程以建立組件，這樣便會增加所有字串的總大小，進而可能超過限制。 若要解決這個問題，您可以將結構描述和/或對應放入不同的 Biztalk 專案 (通常在相同的方案之下) 來重新組織專案，讓每個專案中所有字串的總大小不超過 16 MB。  
  
 您建立的對應可以轉換或轉譯資料，而這些對應可專用於單一交易夥伴，或是用於多個交易夥伴。 本節中的主題介紹與對應結構描述相關的概念。 如需地圖的背景資訊，請參閱 <<c0> [ 對應](../core/maps.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [對應中的連結](../core/links-in-maps.md)  
  
-   [對應中的運算質](../core/functoids-in-maps.md)  
  
-   [對應編譯和測試](../core/map-compilation-and-testing.md)