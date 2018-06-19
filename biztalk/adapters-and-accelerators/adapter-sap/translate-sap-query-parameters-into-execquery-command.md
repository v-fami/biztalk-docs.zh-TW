---
title: SAP 查詢參數轉譯 mySAP 配接器在 BizTalk 中 EXECQUERY 命令 |Microsoft 文件
description: 要轉譯之範例 EXECQUERY，SAP 查詢的指導方針
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a545e20-2607-4946-a60d-0a227b86d093
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efb50db3e499970c0504f81467d382aee31c868f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217726"
---
# <a name="translate-sap-query-parameters-into-execquery-command"></a>SAP 查詢參數轉譯 EXECQUERY 命令
說明如何查詢的參數將轉譯成 EXECQUERY 命令文字。 本主題會使用自訂的 SAP 查詢，ZQUERY_TST_NEW 的範例。  
  
## <a name="open-the-query-in-sap-gui"></a>SAP GUI 中開啟查詢  
 執行下列步驟來開啟 SAP 中的查詢。 此處提供的步驟 ZQUERY_TST_NEW 查詢，而特定 SAP 版本。  
  
1.  執行交易 SQ01。  
  
2.  在**使用者群組中的查詢**頁面上，按一下**快速檢視器**。  
  
3.  在**快速檢視器**頁面上，於**快速檢視**文字方塊中，輸入`ZQUERY_TST_NEW`，然後按一下 **顯示**。  
  
4.  在**快速檢視器**頁面上，按一下**選取項目欄位**索引標籤，列出查詢中的所有參數。  
  
     下圖顯示在查詢定義的所有參數。  
  
     ![SAP 查詢的參數清單](../../adapters-and-accelerators/adapter-sap/media/sap-query-param-types.gif "sap_query_param_types")  
  
5.  按一下 **[執行]**。 會顯示下列頁面。  
  
     ![提供 SAP 查詢的參數值](../../adapters-and-accelerators/adapter-sap/media/sap-query-all-params.gif "sap_query_all_params")  
  
6.  按一下黃色箭號，以定義每個參數。 您可以定義特定允許/非-允許的值，或者您可以定義可允許/非-容許值的範圍。  必須根據每個參數的 SAP GUI 中設定的值，指定 EXECQUERY 語法。  
  
 下一節提供有關 SAP GUI 中值的定義方式以及如何將這些值轉譯成 EXECQUERY 語法說明。  
  
## <a name="frame-an-execquery-syntax"></a>框架 EXECQUERY 語法  
 讓我們看看什麼 EXECQUERY 語法看起來像為基礎的查詢定義中定義的參數值。 若要了解，我們將示範第一個參數，這些值的設定方式的範例**兩位數字**，轉譯成**ZQUERY_TST_NEW**查詢。  
  
 首先，我們假設中的值**單一 vals**  索引標籤 （以綠色的點） 會定義下列螢幕擷取畫面所示：  
  
 ![查詢接受的參數值清單](../../adapters-and-accelerators/adapter-sap/media/sap-query-param-val.gif "sap_query_param_val")  
  
> [!NOTE]
>  按一下黃色箭頭之後，就會出現此對話方塊**兩位數字**參數。  
  
 在這種情況下，EXECQUERY 語法看起來像：  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5'  
```  
  
 相同查詢中，除了中的值**單一 vals**  索引標籤 （以綠色點），您也可以讓這些值**單一 vals**  索引標籤 （具有一個紅點） 定義如下所示：  
  
 ![查詢不接受的參數值清單](../../adapters-and-accelerators/adapter-sap/media/2af88a57-4ff6-4bcc-8961-0f25dbfb8166.gif "2af88a57-4ff6-4bcc-8961-0f25dbfb8166")  
  
 在這種情況下，EXECQUERY 語法如下所示：  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5', NOT @P1 = '6', NOT @P1 = '8'  
```  
  
 現在，如果您新增值以**範圍** 索引標籤 （以綠色點），例如下列螢幕擷取畫面所示：  
  
 ![查詢接受的參數值的範圍](../../adapters-and-accelerators/adapter-sap/media/74907c7d-5a7a-4a2d-a614-6a835eca1764.gif "74907c7d-5a7a-4a2d-a614-6a835eca1764")  
  
 EXECQUERY 語法看起來像：  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5', NOT @P1 = '6', NOT @P1 = '8', @P1 BETWEEN '2' and '5'  
```  
  
 同樣地，如果您新增值以**範圍**索引標籤 （一個紅點），例如下列螢幕擷取畫面所示：  
  
 ![查詢不接受的參數值的範圍](../../adapters-and-accelerators/adapter-sap/media/ccc6a7bb-bc47-4325-8b58-094201f791bf.gif "ccc6a7bb-bc47-4325-8b58-094201f791bf")  
  
 EXECQUERY 語法看起來像：  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5', NOT @P1 = '6', NOT @P1 = '8', @P1 BETWEEN '2' and '5', NOT @P1 BETWEEN '6' AND '8'  
```  
  
 為了簡化和了解，本主題只討論的第一個參數，關於**兩位數字**。 您可以使用類似的方法來判斷如何針對其他參數定義的值轉譯成 EXECQUERY 語法。  
  
