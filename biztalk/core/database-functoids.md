---
title: "資料庫運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77bc9390-cdb5-42ff-8b28-6265c51c79fc
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b68a924fba60d4f0162e80dde0ab06b515765558
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="database-functoids"></a>資料庫運算質
**資料庫**運算質擷取輸出執行個體訊息中使用的資料庫中的資料。 

## <a name="overview"></a>概觀
下列是一份**資料庫**運算質，並使用它們：  
  
-   **資料庫尋查。** 使用**資料庫尋查**運算質從資料庫中擷取資訊，並將它儲存為 Microsoft ActiveX Data Objects.NET (ADO.NET) 資料錄集。 此運算質需要四個依照下列順序的輸入參數：  
  
    -   尋查值  
  
    -   資料庫連接字串  
  
    -   資料表名稱  
  
    -   尋查值的資料行名稱。  
  
-   **傳回錯誤。** 使用**錯誤傳回**運算質擷取錯誤的相關資訊，例如資料庫連線失敗，在執行階段發生。 此運算質需要一個輸入的參數： 從連結**資料庫尋查**運算質。  
  
-   **格式訊息。** 使用引數替代，也可能使用識別碼和交互參照值，傳回格式化和當地語系化的字串。  
  
-   **取得應用程式識別碼。** 擷取應用程式物件的識別碼。  
  
-   **取得應用程式值。** 擷取應用程式值。  
  
-   **取得通用識別碼。** 擷取通用物件的識別碼。  
  
-   **取得通用值。** 擷取通用值。  
  
-   **移除應用程式識別碼。** 移除應用程式值。  
  
-   **設定通用識別碼。** 設定和傳回通用物件的識別碼。  
  
-   **值擷取程式 」。** 使用**值擷取程式 」**從指定的資料行中所傳回的資料錄集擷取資料的運算質**資料庫尋查**運算質。 此運算質需要兩個輸入參數： 連結**資料庫尋查**運算質和資料行名稱。  
  
 七**資料庫**運算質 —**格式訊息，取得應用程式識別碼**，**取得應用程式值**，**取得通用識別碼**， **取得通用值**，**移除應用程式識別碼**，和**設定通用識別碼**— 是**CrossReferencing**運算質。 這些運算質會將輸入訊息的識別碼和值轉譯為輸出訊息所需的識別碼和值。 如需詳細資訊，請參閱**資料庫運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 

## <a name="example"></a>範例  
 下列範例會使用的部分**資料庫**運算質。 假設一個大型零售製造商有遍佈各地的門市。 要追蹤的存放區，總部每個的門市指派唯一的程式碼呼叫**StoreID**。 此外，總部將以下資訊與每個**StoreID**:  
  
-   StoreName  
  
-   StoreAddress  
  
-   City  
  
-   PostalCode  
  
-   StorePhoneNumber  
  
-   StoreManager  
  
 此資訊儲存在資料庫中並定期散發給交易夥伴。 對於製造商而言，所有採購是由總部完成，而非門市。 當總部寄送訂單給交易夥伴時，多家門市收到單一訂單所訂購的商品是很平常的。 而不是傳送要接收商品每個存放區的名稱和位址資訊，總部僅傳送**StoreID**。 若要將名稱和地址資訊插入進階的交貨通知，交易夥伴會使用**資料庫**運算質可自動插入輸出執行個體訊息中的這項資訊。 下圖顯示交易夥伴如何在對應中實作 StoreID 的取代。  
  
 ![將顯示不同資料庫運算質的對應。] (../core/media/origdbfunctoids.gif "origdbfunctoids")  
  
 在圖中，來源結構描述代表內送訂單，而目的結構描述代表進階交貨通知。 **資料庫尋查**運算質會尋找適當的記錄，從適當的資料庫資料表。 **值擷取程式 」**運算質從尋查記錄擷取適當的資料行。 **錯誤傳回**運算質在執行階段會輸出包含錯誤資訊，如果發生錯誤 （例如連接失敗） 的字串。  
  
 在上述範例中，第一個輸入的參數取自**StoreID**欄位的內送訂單，及剩餘三個輸入的參數是設定中的常數**設定\<運算質 > 運算質**對話方塊的 **資料庫尋查**運算質。 也可以從來源結構描述建立連結，為所有四個輸入參數提供值。  
  
> [!NOTE]
>  * 您無法使用某些 Microsoft SQL Server 資料類型，例如**文字**， **ntext**，和**映像**，查詢值當做**資料庫尋查**運算質。 運算質需要可用文字字串表示的資料型別。  
>
>  * 如果沒有相符的輸入的參數的多筆記錄**資料庫尋查**運算質，**值擷取程式 」**運算質只會從第一個記錄擷取資料。  
>
>  * 使用 NT 驗證連接字串保護加密的密碼。  

## <a name="available-functoids"></a>可用的運算質  
 **資料庫**運算質為： 

* 資料庫尋查
* 錯誤傳回
* 格式訊息
* 取得應用程式識別碼
* 取得應用程式值
* 取得通用識別碼
* 取得通用值
* 移除應用程式識別碼
* 設定通用識別碼
* 值擷取程式

如需有關這些 functiods 的詳細資訊，請參閱**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

## <a name="see-also"></a>另請參閱  
-  [如何新增基本運算質至對應](../core/how-to-add-basic-functoids-to-a-map.md)   
-  **資料庫運算質參考**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]