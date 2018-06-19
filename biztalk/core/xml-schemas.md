---
title: XML 結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1ec364e7-866d-4164-be91-be75a40ce878
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86760d50b729419f31ba8186033181e0d03ad14c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008095"
---
# <a name="xml-schemas"></a>XML 結構描述
XML 結構描述會說明以 XML 呈現的商務文件。 因為 Microsoft BizTalk Server 會使用 XML 做為其標準表示商務文件，所以輸入和輸出文件不需要進行任何轉譯。 可以在 BizTalk 編輯器中只使用所有結構描述內均提供的基本屬性組來建立 XML 結構描述，而不需啟用任何的結構描述編輯器延伸模組。  
  
 有幾種的方式，您可以在其中建立 BizTalk Server 中的 XML 結構描述。 其中包括：  
  
-   **建立新的結構描述**。 此種建立結構描述的方法涉及將結構描述新增到 BizTalk 專案。 在**方案總管] 中**、 以滑鼠右鍵按一下 BizTalk 專案、 按一下**新增**，按一下**新項目**，然後按一下 [**結構描述**。 在結構描述樹狀結構檢視中新增各種節點來建置結構描述的結構。  
  
-   **建立新的結構描述中，搭配其他結構描述**。 對於實際上複雜的結構描述，您更有可能會使用其他現有結構描述所提供的類型，來建置訊息的結構描述。 藉由使用 XML 結構描述定義 (XSD) 語言的匯入、包括和重新定義結構描述等概念，您便可以利用其他結構描述中已經定義的類型。 如需有關如何同時使用多個結構描述的詳細資訊，請參閱[使用其他結構描述的](../core/schemas-that-use-other-schemas.md)。  
  
-   **從執行個體訊息產生結構描述**。 您可以產生對應於特定執行個體訊息的 XML 結構描述，只要該特定執行個體訊息是由格式正確的 XML 組成即可。 使用**新增產生的項目-  *\<BizTalk 專案名稱\>*** 對話方塊中，按一下，即可存取**新增產生的項目**上**專案**功能表上，若要執行這種類型的結構描述產生作業。  
  
    > [!NOTE]
    >  此類型的產生作業僅可用於產生 XML 結構描述，不可用於屬性結構描述或一般檔案結構描述。  
  
-   **將結構描述從舊版的結構描述規格語言移轉至 XSD**。 您可以從使用舊版的 XML 資料精簡 (XDR) 格式儲存結構描述的 BizTalk Server 所開發的結構描述，以便讓 BizTalk Server 產生的 XML 結構描述。 如需如何將較舊的 XDR 結構描述移轉至 BizTalk Server 所使用的 XSD 格式的詳細資訊，請參閱[從先前舊版 BizTalk Server 移轉結構描述](../core/schema-migration-from-previous-versions-of-biztalk-server.md)。  
  
     您也可以從使用文件類型定義 (DTD) 語法表示的文件結構描述，根據 XSD 來產生 XML 結構描述。  
  
     使用**新增產生的項目-  *\<BizTalk 專案名稱\>*** 對話方塊中，按一下，即可存取**新增產生的項目**上**專案**功能表上，若要執行這種類型的結構描述產生作業。  
  
    > [!NOTE]
    >  這些類型的產生作業僅可用於產生 XML 結構描述，不可用於屬性結構描述或一般檔案結構描述。  
  
 無論您使用何種結構描述建立技術，都需要繼續修改結構描述，以便充分提供對應執行個體訊息的完整描述。 若要開始這些工作，請參閱[管理內結構描述節點](../core/managing-the-nodes-within-a-schema.md)，[設定節點屬性](../core/how-to-set-node-properties.md)，和[使用現有的節點](../core/working-with-existing-nodes.md)。  
  
## <a name="see-also"></a>請參閱  
 [不同類型的 BizTalk 結構描述](../core/different-types-of-biztalk-schemas.md)