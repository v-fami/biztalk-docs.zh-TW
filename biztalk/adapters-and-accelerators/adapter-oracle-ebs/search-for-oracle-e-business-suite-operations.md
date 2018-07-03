---
title: 搜尋 Oracle E-business Suite 作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2970ddd4-a534-4da4-9bd5-28bb9da4deca
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e861f23a13f6c3e7d5ac500de3b7750429a9cfd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977207"
---
# <a name="search-for-oracle-e-business-suite-operations"></a>搜尋 Oracle E-business Suite 作業
您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]搜尋 Oracle E-business Suite 中的特定成品。 此主題提供有關如何針對不同的檢視，以及支援搜尋萬用字元可以用來搜尋 Oracle 成品。 本主題也提供如何使用搜尋資訊[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  


  
> [!NOTE]
>  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]而[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]呈現基本上相同的介面，當您瀏覽和搜尋作業，因此這兩個元件所述的相同的主題。  
  
 如需詳細資訊，請參閱[搭配使用 SharePoint 與 Oracle E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/use-the-oracle-e-business-suite-adapter-with-sharepoint.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您可以搜尋目標作業的中繼資料之前，您必須連接到 Oracle E-business Suite。 如需如何連接到 Oracle 資料庫使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[連接到 Oracle E-business Suite，在 Visual Studio 中](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)。  
  
## <a name="support-for-wildcard-characters"></a>支援萬用字元  
 搜尋 Oracle E-business Suite 中繼資料使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，則[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]搜尋運算式中支援萬用字元和逸出字元。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|_ (底線)|完全符合一個字元<br /><br /> 比方說，A_ 比對 AB、 AC、 AD。|  
|%（百分比）|比對零或多個字元。<br /><br /> 例如，%比對的 AB，ABC。|  
|\ （逸出）|逸出的特殊意義的 %和 _<br /><br /> 例如，A\\_km 符合 A_B。|  
  
> [!NOTE]
>  Put 之前使用萬用字元來表示，應該將萬用字元解譯成正規字元，而不是萬用字元的字元逸出字元。  
  
## <a name="searching-under-different-views"></a>搜尋不同的檢視  
 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]而[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將資料分類成三個檢視 — 應用程式為基礎的檢視、 成品為基礎的檢視和結構描述為基礎的檢視。 將底下這三個檢視成品的原因之一是以便根據您要搜尋的搜尋。 下表描述如何搜尋可能在這些檢視跨不同。  
  
|檢視|如何搜尋|  
|----------|-------------------|  
|**應用程式為基礎的檢視**|此檢視是由 Oracle E-business Suite 應用程式名稱來分類。 當您知道哪些應用程式包含您想要使用的成品時，您必須使用此檢視。<br /><br /> 使用此檢視的使用者不會感到陌生 Oracle 應用程式，並已了解他們想要使用哪些應用的程式。 因此，在此檢視下的搜尋支援只能在即時運算的層級。 例如，如果**應用程式為基礎的檢視**選取節點時，使用者可以搜尋 Oracle E-business Suite 中的應用程式。 同樣地，如果**介面資料表**選取節點時，使用者可以搜尋 Oracle E-business 應用程式中的介面資料表。|  
|**成品為基礎的檢視**|此檢視是由 Oracle E-business Suite 成品分類。 當使用 Oracle E-business Suite 應用程式成品，使用者必須使用此檢視，當他們知道他們想要使用，但不確定哪個應用程式成品屬於哪一個 Oracle E-business Suite 成品。<br /><br /> 使用此檢視，使用者可以搜尋特定成品 Oracle E-business Suite 的所有應用程式。 例如，使用者可以選取**Interface Table**節點，並使用字串的搜尋`AR%`。 這是如何執行搜尋：<br /><br /> -因為介面資料表會進一步分類底下的應用程式，將會列出所有的應用程式的開頭 AR。<br />-所有開頭為 AR 的介面資料表會列出。 這些資料表可以屬於任何 Oracle E-business suite 應用程式。<br /><br /> 當使用 Oracle 資料庫成品使用此檢視，使用者可以搜尋特定成品是您登入目前的結構描述或所有結構描述下。 比方說，如果使用者想要使用一個程序 CREATE_ACCOUNT，但不是知道哪一個結構描述的程序所屬，他們可以選取**所有結構描述**節點，然後使用字串的搜尋`CREATE%`。|  
|**結構描述為基礎的檢視**|此檢視會依基礎的 Oracle 資料庫中可用的結構描述分類。 當您知道哪一個結構描述具有您想要使用的成品時，您必須使用此檢視。<br /><br /> 使用此檢視的使用者不會感到陌生結構描述中有他們想要使用的成品。 因此，在此檢視下的搜尋支援只能在即時運算的層級。 例如，如果**結構描述為基礎的檢視**選取節點時，使用者可以搜尋 Oracle 資料庫中的結構描述。 同樣地，如果**資料表**選取節點時，使用者可以搜尋 Oracle E-business 應用程式中的資料表。|  
  
## <a name="searching-for-operations"></a>搜尋作業  
 要搜尋的中繼資料中使用 Oracle E-business Suite [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，執行下列步驟。  
  
#### <a name="to-search-metadata-in-oracle-e-business-suite"></a>搜尋 Oracle E-business Suite 中的中繼資料  
  
1. 連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Oracle E-business Suite，在 Visual Studio 中](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**清單中，選取 根據您要搜尋的輸入或輸出作業的合約型別。  
  
3. 在 **選取一個類別**方塊中，按一下您要在其下搜尋特定成品的類別目錄節點。 例如，若要搜尋 Oracle 應用程式，請按一下**應用程式為基礎的檢視**節點。  
  
   > [!NOTE]
   >  若要搜尋應用程式中，您可以指定好記的名稱或應用程式的簡短名稱。 例如，若要搜尋**應收帳款**應用程式，您可以為指定搜尋字串`Receive%`或`AR`。 AR 是應用程式的簡短名稱。  
  
4. 在 **分類中的搜尋**方塊中，輸入要搜尋特定成品的搜尋運算式。 例如，若要搜尋其名稱中有 「 客戶 」 的 Oracle 應用程式，請輸入`%Customer%`。  
  
   > [!NOTE]
   >  搜尋字串會區分大小寫。  
  
5. 若要開始搜尋，請按一下向右箭號圖示的按鈕。 搜尋完成後**可用的類別和作業**方塊會列出符合搜尋準則的成品。  
  
    下圖顯示其名稱中包含 「 客戶 」 的 Oracle 應用程式資料表。  
  
    ![Oracle E 中搜尋中繼資料&#45;Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/media/e6278992-a475-4a35-8371-db862f25a720.gif "e6278992-a475-4a35-8371-db862f25a720")  
  
   > [!NOTE]
   >  要搜尋的並行程式中，您可以指定好記的名稱或並行處理程式的實際名稱。 例如，若要搜尋**客戶介面**並行處理程式，您可以為指定的搜尋字串`%Customer Interface%`或`%RACUST%`。 RACUST 是並行處理程式的實際名稱。  
   >   
   >  此外，搜尋結果永遠包含標準的並行程式，不論其名稱是否符合指定的搜尋字串。  
  
## <a name="see-also"></a>另請參閱  
 [瀏覽、 搜尋及取得 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)