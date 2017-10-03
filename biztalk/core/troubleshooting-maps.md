---
title: "地圖疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32e2eb52-6740-4cf5-82ec-3b6d0b784276
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbb5800ba076184f09f0159f030a44e169ac742b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-maps"></a>地圖疑難排解
本主題提供對應的疑難排解策略、問題細節和解決方法資訊。  
  
## <a name="troubleshooting-strategies"></a>疑難排解的策略  
  
### <a name="validate-your-map"></a>驗證您的對應  
 這點可能看似明顯，不過您永遠都應該在開發整個對應的不同點對其進行驗證。 這樣將會有助於在開發週期的早期識別設計、邏輯和結構描述問題，以便及早修正這些問題，或是找出替代的解決方案。  
  
##### <a name="to-validate-a-biztalk-map"></a>驗證 BizTalk 對應  
  
1.  在 [方案總管] 中開啟您想驗證的對應。  
  
2.  在方案總管 中，以滑鼠右鍵按一下地圖上，然後**驗證對應**。  
  
3.  在 [輸出] 視窗中驗證結果。  
  
> [!NOTE]
>  在驗證對應時，並不會檢查測試執行個體資料是否違反在結構描述中定義的任何資料型別。 在 [BizTalk 編輯器] 中測試對應或驗證執行個體資料時，您可以檢查執行個體資料。  
  
### <a name="review-the-xslt-generated-for-your-map"></a>檢閱您的對應所產生的 XSLT  
 檢查對應編譯器產生的 XSLT 通常很有用。 查看 XSLT 的優點包括：  
  
-   如果您使用迴圈或自訂運算質，將更瞭解迴圈執行的方式以及自訂運算質叫用的方式。  
  
-   如果您有已編譯的對應，檢閱 XSLT 可讓您查看對應如何編譯為轉換，並且知道如何以更好的方式建構、取代或簡化一個或多個部分。  
  
-   如果您要使用自訂的指令碼或其他成品，檢閱 XSLT 可讓您查看指令碼、成品和其他對應部分互動的方式。  
  
 幸而，檢視對應的 XSLT 是很容易的程序。  
  
##### <a name="to-view-the-xslt-generated-by-the-map-compiler"></a>檢視對應編譯器產生的 XSLT  
  
1.  從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，按一下 [**方案總管] 中**索引標籤上，地圖中，以滑鼠右鍵按一下，然後按一下**驗證對應**。  
  
2.  捲動至 [輸出] 視窗，以尋找 XSL 檔案的 URL。 按 CTRL 再按一下 URL，以檢視檔案。  
  
 如果決定要以手動方式自訂對應，您可以修改對應編譯器所產生的版本。 這些變更不會由對應工具反映，而且會在下一次建置解決方案時遺失。  
  
### <a name="tune-your-map-for-specific-scenarios-using-mapsource"></a>微調您的對應使用為特定案例\<mapsource >  
 您可以藉由修改屬性來修改對應工具的一些預設行為**mapsource**直接在對應來源 (.btm) 檔案中的項目。 目前您可以修改三種行為：  
  
-   **最佳化值對應運算質程式碼產生**。 您可以修改控制變數搭配 `if` 陳述式使用時的行為。  
  
-   **配合佔用空間很大的結構描述**。 您可以變更內部編譯器節點在大型對應中使用的方式。  
  
-   **管理迴圈 」、 「 條件 」 和 「 值對應運算質的 for-each 用法**。 您可以控制 `xsl:for-each` 陳述式在目的結構描述內使用的位置。  
  
 如需有關修改**mapsource**，請參閱[管理預設對應工具的行為使用\<mapsource >](../core/managing-default-mapper-behavior-using-mapsource.md)。  
  
## <a name="see-also"></a>另請參閱  
 [一般疑難排解問答集](../core/general-troubleshooting-questions-and-answers.md)   
 [常見的錯誤](../core/common-errors.md)