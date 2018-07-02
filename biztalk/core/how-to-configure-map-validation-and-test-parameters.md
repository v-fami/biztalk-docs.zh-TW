---
title: 如何設定對應驗證和測試參數 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1768918c-e94f-476f-b288-9e030c691177
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7aaa62e74f1c49f2e43d96c7d546af023847d91
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967407"
---
# <a name="how-to-configure-map-validation-and-test-parameters"></a>如何設定對應驗證和測試參數
之前驗證和測試對應時，您必須在中設定對應驗證和測試參數**屬性**對應的視窗。  
  
## <a name="configure-the-map-validation-and-test-parameters"></a>設定對應驗證和測試參數  
  
1.  在 [方案總管] 中，使用滑鼠右鍵按一下您想要設定，然後再按一下其屬性頁**屬性**。  
  
2.  在 [屬性] 視窗中，執行下列步驟：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |**驗證 TestMap 輸入**|設定是否要在測試對應之前，針對來源結構描述驗證執行個體訊息。|  
    |**驗證 TestMap 輸出**|設定是否要在測試對應之後，針對目的結構描述驗證執行個體訊息。|  
    |**TestMap 輸入執行個體**|設定測試對應時要使用的執行個體訊息資料的位置。<br /><br /> 如果您設定這個屬性時，您也必須設定**TestMap 輸入**屬性。|  
    |**TestMap 輸出執行個體**|設定想要儲存測試對應作業輸出檔案的位置。<br /><br /> 如果您設定這個屬性時，您也必須設定**TestMap 輸出**屬性。|  
    |**TestMap 輸入**|設定輸入執行個體資料格式。|  
    |**TestMap 輸出**|設定測試對應時要使用的輸出資料型別。|  
  
    > [!IMPORTANT]
    >  若要測試對應，首先必須設定對應的屬性。  

在開發您的對應之後，接下來的步驟之一就是要對其進行驗證。 此主題提供驗證對應的逐步說明。  
  
## <a name="validate-a-biztalk-map"></a>驗證 BizTalk 對應  
  
1.  在 [方案總管] 中開啟您想驗證的對應。  
  
2.  在 [方案總管] 中，以滑鼠右鍵按一下地圖，然後按**驗證對應**。  
  
3.  在 [**輸出**] 視窗中，驗證結果。  
  
> [!IMPORTANT]
>  若您在輸出中使用自訂資料或常數，則必須確認來源測試資料和目標常數值的資料型別是否有效。 當您驗證對應時，BizTalk 對應工具不會檢查的執行個體資料是否違反在結構描述中定義的任何資料型別。 在您使用「BizTalk 編輯器」測試對應或驗證執行個體資料時，已完成此項檢查。 

## <a name="test-a-biztalk-map"></a>測試 BizTalk 對應

在開發對應之後，以下其中一個步驟是進行測試。 本主題提供測試對應的逐步指示，包括檢視對應編譯器產生之 XSLT 的步驟。  
  
1.  在 方案總管 中，以滑鼠右鍵按一下您想要測試，然後選取 的地圖**測試對應**。  
  
2.  驗證會導致**輸出**視窗。  
  
    > [!IMPORTANT]
    >  建議您在測試對應之前，先在 [屬性] 視窗上設定輸入和輸出執行個體屬性。  
  
## <a name="review-the-xslt"></a>檢閱 XSLT  
 檢查對應編譯器產生的 XSLT 通常很有用。 查看 XSLT 的優點包括：  
  
- 如果您使用迴圈或自訂運算質，將更瞭解迴圈執行的方式以及自訂運算質叫用的方式。  
  
- 如果您有複雜的對應，檢視 XSLT 可讓您查看對應如何編譯為轉換，而且可能會提供深入解析如何更好的結構、 取代或簡化一個或多個部分。  
  
- 如果您要使用自訂的指令碼或其他成品，檢閱 XSLT 可讓您查看指令碼、成品和其他對應部分互動的方式。  
  
  換句話說，檢視 XSLT 是一個偵錯對應的好方法。  
  
#### <a name="view-the-xslt-generated-by-the-map-compiler"></a>檢視對應編譯器產生的 XSLT  
  
1.  從 Visual Studio BizTalk 專案中，選取**方案總管**索引標籤上，以滑鼠右鍵按一下對應，然後選取**驗證對應**。  
  
2.  捲動至 [輸出] 視窗，以尋找 XSL 檔案的 URL。 按下**CTRL**，然後選取要檢視檔案的 URL。  
  
> [!NOTE]
>  XSL 檔案所做的變更不會反映在對應中，並在下次建置就會覆寫。  
  
## <a name="see-also"></a>另請參閱  

[如何偵錯對應](../core/how-to-debug-maps.md)  
[地圖疑難排解](../core/troubleshooting-maps.md)  