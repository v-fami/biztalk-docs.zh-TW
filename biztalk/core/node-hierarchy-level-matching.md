---
title: "節點階層層級比對 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Field nodes
- BizTalk Mapper, processing
- Record node
- BizTalk Mapper, compiler directives
- destination schemas, matching nodes
- source schemas, matching nodes
- maps, links
- Target Links property
- BizTalk Mapper, links
- compiler directives, matching schema nodes
- compiler directives, flattening source hierarchies
- maps, processing
ms.assetid: 5ba1ac77-0e70-4c58-9b8c-1b379dbbb3bd
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b2d0c363abfefb9e3d0eb8abfb332c59539bb67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="node-hierarchy-level-matching"></a>節點階層層級比對
BizTalk 對應工具可讓您設定連結屬性以控制編譯器與來源與目的結構描述之間的節點階層比對的方式。 當您在來源結構描述的欄位與目的結構描述的欄位之間建立連結時，BizTalk 對應工具會自動新增編譯器連結。 這些編譯器連結視您所選取的比對而定。  
  
 當您在顯示的格線頁中選取的連結時，其中一個屬性顯示在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗是**目標連結**屬性。 您可以為對應中的每個連結選擇以下可能的值：  
  
-   **簡維連結。** 使用此值將所有來源階層簡維至目的結構描述節點中的父記錄。  
  
-   **連結由上往下比對。** 使用此值由結構描述上方至結構描述下方比對節點層級。  
  
-   **比對下往上連結。** 使用此值由結構描述下方至結構描述上方比對節點層級。  
  
## <a name="flatten-links"></a>簡維連結  
 在此模式中，將所有來源階層簡維至目的節點的父記錄。 在第一例中，來源結構描述比目的結構描述較為複雜。 在第二例中，目的結構描述較為複雜。  
  
 ![](../core/media/bts-tls-flatten.gif "bts_tls_flatten")  
簡維連結  
  
 ![](../core/media/bts-tls-flatten-2.gif "bts_tls_flatten_2")  
簡維連結，第二例  
  
## <a name="match-links-top-down"></a>由上往下比對連結  
 此模式由上往下比對層級。 在第一例中，來源結構描述比目的結構描述較為複雜。 在第二例中，目的結構描述較為複雜。  
  
 ![](../core/media/bts-tls-topdown.gif "bts_tls_topdown")  
由上往下比對  
  
 ![](../core/media/bts-tls-topdown-2.gif "bts_tls_topdown_2")  
由上往下比對，第二例  
  
## <a name="match-links-bottom-up"></a>由下往上比對連結  
 此模式由下往上比對層級。 在第一例中，來源結構描述比目的結構描述較為複雜。 在第二例中，目的結構描述較為複雜。  
  
 ![](../core/media/bts-tls-bottomup.gif "bts_tls_bottomup")  
由下往上比對  
  
 ![](../core/media/bts-tls-bottomup-2.gif "bts_tls_bottomup_2")  
由下往上比對，第二例  
  
## <a name="how-biztalk-mapper-processes-link-types"></a>BizTalk 對應工具如何處理連結類型  
 因為您可以設定**目標連結**為不同的連結的不同值的屬性，BizTalk 對應工具需要解決它們衝突時的不同設定的方法。  
  
 例如，如果您使用簡維編譯器指示詞、 由上而下編譯器指示詞和由下往上編譯器指示詞從連結的**欄位**節點**欄位**中目的結構描述，而這些節點節點共用相同的父系**記錄**節點，BizTalk 對應工具會忽略衝突的由上而下和由下往上編譯器指示詞，並將所有連結當作已設定簡維編譯器指示詞。  
  
 下表顯示 BizTalk 對應工具如何處理連結**欄位**中相同的節點**記錄**目的結構描述中的節點為基礎的設定**目標連結**在相同的連結屬性**記錄**節點。  
  
|簡維|由上往下|由下往上|結果|  
|-------------|---------------|----------------|------------|  
|0 或更多|1 或更多|1 或更多|BizTalk 對應工具將所有連結當作已設定為簡維編譯器指示詞。|  
|1 或更多|1 或更多|0|BizTalk 對應工具將所有連結當作已設定為由上往下編譯器指示詞。|  
|1 或更多|0|1 或更多|BizTalk 對應工具將所有連結當作已設定為由下往上編譯器指示詞。|  
  
 由上往下和由下往上編譯器指示詞的優先順序高於簡維編譯器指示詞，但兩者均存在時會相互抵銷。  
  
## <a name="see-also"></a>另請參閱  
 [大量複製運算質](../core/mass-copy-functoid.md)   
 [如何設定來源連結編譯器值](../core/how-to-set-the-source-links-compiler-value.md)   
 [編譯對應](../core/compiling-maps.md)