---
title: "搜尋 Oracle E-business Suite 作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2970ddd4-a534-4da4-9bd5-28bb9da4deca
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 797f89b5032d6bcfdb1a4d16f5a83d53d01f1c7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="search-for-oracle-e-business-suite-operations"></a>搜尋 Oracle E-business Suite 作業
您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]搜尋 Oracle E-business Suite 中的特定成品。 本主題提供有關如何針對不同的檢視，以及支援搜尋的資訊可以使用萬用字元搜尋 Oracle 成品。 本主題也提供如何使用搜尋資訊[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  


  
> [!NOTE]
>  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]呈現基本上相同的介面，當您瀏覽和搜尋作業，因此相同的主題將涵蓋這兩個元件。  
  
 如需詳細資訊，請參閱[搭配 SharePoint 使用 Oracle E-business Suite 介面卡](../../adapters-and-accelerators/adapter-oracle-ebs/use-the-oracle-e-business-suite-adapter-with-sharepoint.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您可以搜尋目標作業的中繼資料之前，您必須連接到 Oracle E-business Suite 的資訊。 如需如何連接到 Oracle 資料庫使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)。  
  
## <a name="support-for-wildcard-characters"></a>支援萬用字元  
 搜尋 Oracle E-business Suite 中繼資料使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]、[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]搜尋運算式中支援萬用字元和逸出字元。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|_ (底線)|完全符合一個字元<br /><br /> 例如，A_ 比對 AB、 AC、 AD。|  
|%（百分比）|比對零個或多個字元。<br /><br /> 例如，%比對 A，AB，ABC。|  
|\ （逸出）|逸出的特殊意義的 %和 _<br /><br /> 例如，A\\_km 符合 A_B。|  
  
> [!NOTE]
>  逸出字元是會放置在使用萬用字元來表示，應該將萬用字元解譯成正規字元，而不是萬用字元前面的字元。  
  
## <a name="searching-under-different-views"></a>搜尋不同的檢視  
 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]分類成三個檢視的資料，應用程式為基礎的檢視、 成品為基礎的檢視和結構描述為基礎的檢視。 其中一個原因來分類底下這三個檢視成品是有助於根據您要搜尋的搜尋。 下表描述如何搜尋可在這些檢視之間會有所不同。  
  
|檢視|如何搜尋|  
|----------|-------------------|  
|**應用程式為基礎的檢視**|此檢視會由 Oracle E-business Suite 應用程式名稱來分類。 當您知道哪一個應用程式包含您想要使用的成品時，您必須使用此檢視。<br /><br /> 使用此檢視的使用者會很熟悉 Oracle 應用程式，而且了解他們想要使用哪個應用的程式。 因此，在此檢視下的搜尋支援只能在即時運算層級。 例如，如果**應用程式為基礎的檢視**選取節點時，使用者可以搜尋 Oracle E-business Suite 中的應用程式。 同樣地，如果**介面資料表**選取節點時，使用者可以搜尋 Oracle E-business 應用程式中的介面資料表。|  
|**成品為基礎的檢視**|此檢視是由 Oracle E-business Suite 成品分類。 當使用 Oracle E-business Suite 應用程式成品，則使用者必須使用此檢視時才會知道他們想要使用，但不確定哪個應用程式成品屬於哪一個 Oracle E-business Suite 成品。<br /><br /> 使用此檢視，使用者可以搜尋特定的成品 Oracle E-business Suite 的所有應用程式。 例如，使用者可以選取**介面資料表**節點，並使用字串的搜尋`AR%`。 這是會在執行搜尋的方式：<br /><br /> -因為介面資料表會進一步分類底下的應用程式，將會列出所有開頭 AR 的應用程式。<br />-所有開頭為 AR 的介面資料表會列出。 這些資料表可以屬於任何 Oracle E-business suite 應用程式。<br /><br /> 當使用 Oracle 資料庫成品使用此檢視，使用者可以搜尋特定的成品是您登入的目前結構描述或所有結構描述下。 例如，如果使用者想要使用哪一個結構描述的程序 CREATE_ACCOUNT 但不是認得所屬的程序，他們可以選取**所有結構描述**節點，然後使用字串的搜尋`CREATE%`。|  
|**結構描述為基礎的檢視**|此檢視會以基礎的 Oracle 資料庫中可用的結構描述分類。 當您知道哪一個結構描述具有您想要使用的成品時，您必須使用此檢視。<br /><br /> 使用此檢視的使用者將無法熟悉擁有他們想要使用的成品的結構描述。 因此，在此檢視下的搜尋支援只能在即時運算層級。 例如，如果**結構描述為基礎的檢視**選取節點時，使用者可以搜尋 Oracle 資料庫中的結構描述。 同樣地，如果**資料表**選取節點時，使用者可以搜尋 Oracle E-business 應用程式中的資料表。|  
  
## <a name="searching-for-operations"></a>搜尋作業  
 要搜尋的中繼資料中使用 Oracle E-business Suite [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，執行下列步驟。  
  
#### <a name="to-search-metadata-in-oracle-e-business-suite"></a>搜尋 Oracle E-business Suite 中的中繼資料  
  
1.  連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**清單中，選取 根據您要搜尋的輸入或輸出作業的合約的型別。  
  
3.  在**選取類別目錄**方塊中，按一下您要在其下搜尋特定的成品的類別目錄節點。 例如，若要搜尋 Oracle 應用程式，請按一下**應用程式為基礎的檢視**節點。  
  
    > [!NOTE]
    >  若要搜尋應用程式中，您可以指定好記的名稱或應用程式的簡短名稱。 例如，若要搜尋**應收帳款**應用程式，您可以指定搜尋字串為`Receive%`或`AR`。 AR 是應用程式的簡短名稱。  
  
4.  在**類別目錄中的搜尋**方塊中，輸入要搜尋特定的成品搜尋運算式。 例如，若要搜尋其名稱中具有 「 客戶 」 的 Oracle 應用程式，請輸入`%Customer%`。  
  
    > [!NOTE]
    >  搜尋字串會區分大小寫。  
  
5.  若要開始搜尋，請按一下向右箭號圖示的按鈕。 搜尋完成之後，**可用的類別和作業**方塊會列出符合搜尋準則的成品。  
  
     下圖顯示其名稱中包含 「 客戶 」 的 Oracle 應用程式資料表。  
  
     ![搜尋 Oracle &#45; 中的中繼資料Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/media/e6278992-a475-4a35-8371-db862f25a720.gif "e6278992-a475-4a35-8371-db862f25a720")  
  
    > [!NOTE]
    >  要搜尋並行程式，您可以指定好記的名稱或並行處理程式的實際名稱。 例如，若要搜尋**客戶介面**並行程式，您可以指定搜尋字串為`%Customer Interface%`或`%RACUST%`。 RACUST 是並行程式的實際名稱。  
    >   
    >  此外，搜尋結果永遠包含標準的並行程式，不論其名稱是否符合指定的搜尋字串。  
  
## <a name="see-also"></a>另請參閱  
 [瀏覽、 搜尋及取得 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)