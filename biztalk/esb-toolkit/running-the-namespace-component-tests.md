---
title: 執行命名空間元件測試 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 13768608-ade6-44c0-897f-d417c3408302
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0ae865e91fd6ff796cb870c71840bde8a95831e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294934"
---
# <a name="running-the-namespace-component-tests"></a>執行測試命名空間元件
下列程序顯示如何執行所有的四個測試案例，以供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]命名空間元件 」 範例。  
  
 **若要執行範例測試案例的命名空間元件**  
  
1.  您第一次執行此範例之前，請確定該接收位置和傳送連接埠 URL 指向來源發佈檔案中的適當子資料夾。 指定接收位置的子資料夾 \Source\Samples\Namespace\Test\Filedrop\In 和子資料夾 \Source\Samples\Namespace\Test\Filedrop\Out 傳送連接埠的 url。  
  
2.  如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。  
  
3.  建立名為 TEST_Add_to_PassThrough.0000.ns.xml （位於您 ESB 的安裝資料夾的 \Source\Samples\Namespace\Test\Data\ 子資料夾），檔案的副本，並重新命名該複本移除"TEST_"前置詞。  
  
4.  將重新命名的檔案複製到 \Source\Samples\Namespace\Test\Filedrop\In 子資料夾。  
  
5.  ESB 拾取訊息、 新增命名空間，和將更新的訊息置放 \Source\Samples\Namespace\Test\Filedrop\Out 子資料夾。 開啟 輸入及輸出檔案中 文字編輯器，以查看這項測試的影響。  
  
6.  現在，執行第二個測試。 建立一份名為 TEST_Add_to_Remove.0000.ns.xml 檔案並將它重新命名藉由移除"TEST_"前置詞。  
  
7.  將重新命名的檔案複製到 \Source\Samples\Namespace\Test\Filedrop\In 子資料夾。  
  
8.  ESB 拾取訊息、 命名空間加入、 移除新的命名空間，及將更新的訊息置放 \Source\Samples\Namespace\Test\Filedrop\Out 子資料夾。 開啟 輸入及輸出檔案中 文字編輯器，以查看這項測試的影響。  
  
9. 現在，執行第三個測試。 建立一份名為 TEST_PassThrough_to_Remove.0000.ns.xml 檔案並將它重新命名藉由移除"TEST_"前置詞。  
  
10. 將重新命名的檔案複製到 \Source\Samples\Namespace\Test\Filedrop\In 子資料夾。  
  
11. ESB 拾取訊息、 移除現有的命名空間，並將更新的訊息置放 \Source\Samples\Namespace\Test\Filedrop\Out 子資料夾。 開啟 輸入及輸出檔案中 文字編輯器，以查看這項測試的影響。  
  
12. 最後，執行第四個測試。 建立一份名為 TEST_AddViaExtraction_to_PassThrough.0000.ns.xml 檔案並將它重新命名藉由移除"TEST_"前置詞。  
  
13. 將重新命名的檔案複製到 \Source\Samples\Namespace\Test\Filedrop\In 子資料夾。  
  
14. ESB 拾取訊息，會擷取在指定的項目**ExtractionNodeXPath**屬性，從指定的命名空間的值，這個項目中建立訊息，並將更新的訊息置放 \Source\Samples\Namespace\Test\Filedrop\Out 子資料夾。 開啟 輸入及輸出檔案中 文字編輯器，以查看這項測試的影響。