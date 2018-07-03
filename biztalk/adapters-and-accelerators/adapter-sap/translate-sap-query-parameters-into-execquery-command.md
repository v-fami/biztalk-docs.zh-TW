---
title: SAP 查詢參數轉譯為 EXECQUERY 命令 mySAP 配接器在 BizTalk 中 |Microsoft Docs
description: 要轉譯範例 EXECQUERY，SAP 查詢的指導方針
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
ms.openlocfilehash: c8ffd480e952e0df7114a93f6cb2a5baf631ad96
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021693"
---
# <a name="translate-sap-query-parameters-into-execquery-command"></a>SAP 查詢參數轉譯為 EXECQUERY 命令
說明如何查詢參數轉譯為 EXECQUERY 命令文字。 本主題會使用自訂的 SAP 查詢，ZQUERY_TST_NEW 的範例。  
  
## <a name="open-the-query-in-sap-gui"></a>在 SAP GUI 中開啟查詢  
 執行下列步驟，以在 SAP 中開啟查詢。 此處提供的步驟適用於 ZQUERY_TST_NEW 查詢，並且專屬於 SAP 版本。  
  
1. 執行交易 SQ01。  
  
2. 在 **查詢，從使用者群組**頁面上，按一下**快速檢視器**。  
  
3. 在 **快速檢視器**頁面上，於**快速檢視**文字方塊中，輸入`ZQUERY_TST_NEW`，然後按一下**顯示**。  
  
4. 在 **快速檢視器**頁面上，按一下**選取項目欄位**索引標籤，列出查詢中的所有參數。  
  
    下圖顯示在查詢定義的所有參數。  
  
    ![SAP 查詢的參數清單](../../adapters-and-accelerators/adapter-sap/media/sap-query-param-types.gif "sap_query_param_types")  
  
5. 按一下 **[執行]**。 會顯示下列頁面。  
  
    ![提供 SAP 查詢的參數值](../../adapters-and-accelerators/adapter-sap/media/sap-query-all-params.gif "sap_query_all_params")  
  
6. 按一下黃色箭號，以定義每個參數。 您可以定義特定允許/非-允許的值，或者您可以定義允許/非-容許值的範圍。  EXECQUERY 語法必須根據每個參數的 SAP GUI 中設定的值指定。  
  
   下一節提供有關 SAP GUI 中定義之值的方式，以及如何將這些值轉譯為 EXECQUERY 語法說明。  
  
## <a name="frame-an-execquery-syntax"></a>框架 EXECQUERY 語法  
 讓我們看看起來像 EXECQUERY 語法基礎查詢定義中所定義的參數值。 若要了解這一點，我們將示範的第一個參數，值的設定方式的範例**二位數字**，來轉譯**ZQUERY_TST_NEW**查詢。  
  
 首先，讓我們假設中的值**單一 vals** （加上一個綠點） 索引標籤會定義下列的螢幕擷取畫面所示：  
  
 ![查詢接受的參數值的清單](../../adapters-and-accelerators/adapter-sap/media/sap-query-param-val.gif "sap_query_param_val")  
  
> [!NOTE]
>  在您按一下的黃色箭頭之後，會出現此對話方塊**二位數字**參數。  
  
 在此情況下，EXECQUERY 語法看起來像：  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5'  
```  
  
 相同查詢中，除了中的值**單一 vals**索引標籤 （具有一個綠點），您可以也在值**單一 vals**  索引標籤 （具有一個紅點） 定義如下所示：  
  
 ![查詢不接受的參數值的清單](../../adapters-and-accelerators/adapter-sap/media/2af88a57-4ff6-4bcc-8961-0f25dbfb8166.gif "2af88a57-4ff6-4bcc-8961-0f25dbfb8166")  
  
 在此情況下，EXECQUERY 語法如下所示：  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5', NOT @P1 = '6', NOT @P1 = '8'  
```  
  
 現在，如果您新增至值**範圍** 索引標籤 （具有一個綠點），如下列螢幕擷取畫面所示：  
  
 ![查詢接受的參數值的範圍](../../adapters-and-accelerators/adapter-sap/media/74907c7d-5a7a-4a2d-a614-6a835eca1764.gif "74907c7d-5a7a-4a2d-a614-6a835eca1764")  
  
 EXECQUERY 語法看起來像：  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5', NOT @P1 = '6', NOT @P1 = '8', @P1 BETWEEN '2' and '5'  
```  
  
 同樣地，如果您新增至值**範圍**索引標籤 （一個紅點），如下列螢幕擷取畫面所示：  
  
 ![查詢不接受的參數值的範圍](../../adapters-and-accelerators/adapter-sap/media/ccc6a7bb-bc47-4325-8b58-094201f791bf.gif "ccc6a7bb-bc47-4325-8b58-094201f791bf")  
  
 EXECQUERY 語法看起來像：  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5', NOT @P1 = '6', NOT @P1 = '8', @P1 BETWEEN '2' and '5', NOT @P1 BETWEEN '6' AND '8'  
```  
  
 為了簡化和了解，本主題只討論的第一個參數，關於**二位數字**。 您可以使用類似的方法來判斷如何定義其他參數的值轉譯為 EXECQUERY 語法。  
  
