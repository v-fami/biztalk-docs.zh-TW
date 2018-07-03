---
title: MethodCall （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, calling
- examples, orchestrations
- orchestrations, methods
ms.assetid: 6bdc72da-9478-403a-b706-3089b7374ac7
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ef3869161c699c48648bc0c22f1d9f40c9bde73
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986869"
---
# <a name="methodcall-biztalk-server-sample"></a>MethodCall （BizTalk Server 範例）
MethodCall 範例示範如何從 BizTalk Server 呼叫 .NET 方法。  

## <a name="what-this-sample-does"></a>此範例的用途  
 此範例使用下列步驟順序和 .NET 方法進行互動：  

1. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程會從 In 資料夾擷取 XML 輸入檔案。 此檔案包含有關您要數學程式庫執行的加法或減法資訊。  

2. 協調程式會呼叫包含的數學程式庫，執行 XML 輸入檔案中指定的加法或減法。  

3. 適當的數學程式庫方法，或是**新增**或**Subtract**、 執行要求的計算和封裝為 XML 文件的結果。  

4. 協調流程會將產生的 .xml 檔案放到 Out 資料夾中。  

## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 此範例示範下列功能：  

-   在協調程式中利用升級的屬性。 InputSchema.xsd 中的三個項目會升級為辨別欄位。 當協調流程收到輸入訊息時，它會取得這三個欄位的值，並將它們指派至協調流程中宣告的對應變數。  

-   使用**決定**」 圖形來表達協調流程中的"if-then-else"邏輯。 協調流程會將辨別欄位的值指派給內部變數之後，即會進入**決定**圖形，以檢查是否應該執行的加法或減法。 如果沒有需要執行的作業，協調流程就會終止。  

-   從協調流程呼叫外部組件。 如果要執行加法，協調流程會呼叫外部 C# 組件，並傳入兩個參數來執行加法。 相同的程序也適用於減法。  

    > [!NOTE]
    >  您必須先將組件安裝至全域組件快取後，才能從協調流程呼叫此組件；否則，您將在執行階段收到 XLANG 錯誤。  

-   使用**訊息指派**圖形來建構輸出訊息。  

-   將下列程式碼放到「運算式」圖形中，來偵錯協調流程：  

    ```  
    System.Diagnostics.Debug.WriteLine(iResult);  
    ```  

     您也可以使用下列程式碼將結果寫入事件記錄：  

    ```  
    System.Diagnostics.EventLog.WriteEntry("MethodCall SDK Sample Debug", System.String.Format("Result = {0}", iResult);  
    ```  

## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*範例路徑*\>\Orchestrations\MethodCall\  

 下表顯示此範例中的檔案，並描述其用途。  


|                                          檔案                                           |                                                                                           描述                                                                                            |
|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                        Cleanup.bat                                         | 用來解除部署組件，以及將它從全域組件快取中移除。 移除傳送埠和接收埠。 視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。 |
|                                         Input.xml                                          |                                                                                        範例輸入檔案。                                                                                        |
|                                         Setup.bat                                          |                                                                            用來建置和初始化此範例。                                                                             |
| 在 \MathLibrary 資料夾中：<br /><br /> AssemblyInfo.cs, MathHelper.cs, MathLibrary.csproj |                                                                此範例所使用之數學程式庫的專案和來源檔案。                                                                |
|       在 \MethodCallSample 資料夾中：<br /><br /> InputSchema.xsd, OutputSchema.xsd       |                                                                    分別為輸入和輸出 .xml 檔案的結構描述。                                                                    |
| 在 \MethodCallSample 資料夾中：<br /><br /> MethodCallSample.btproj, MethodCallSample.sln |                                                                           這個範例的專案及解決方案檔案。                                                                            |
|          在 \MethodCallSample 資料夾中：<br /><br /> MethodCallSampleBinding.xml          |                                                                          用於自動化設定，例如連接埠繫結。                                                                          |
|             在 \MethodCallSample 資料夾中：<br /><br /> MethodCallService.odx             |                呼叫數學程式庫執行要求之計算的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。                |

## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  

#### <a name="to-build-and-initialize-the-methodcall-sample"></a>建置和初始化 MethodCall 範例  

1. 在命令視窗中，瀏覽至下列資料夾：  

    \<*範例路徑*\>\Orchestrations\MethodCall  

2. 執行檔案 Setup.bat，這會執行下列動作：  

   - 在 MethodCall 中建立此範例的輸入 (In) 和輸出 (Out) 資料夾。  

   - 編譯此範例的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案，並部署產生的組件。  

   - 建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置以及傳送埠和接收埠，並將其繫結至協調流程。  

   - 啟用接收位置並啟動傳送埠。 登錄和啟動協調流程。  

> [!NOTE]
>  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。  

## <a name="running-this-sample"></a>執行此範例  

#### <a name="to-run-the-methodcall-sample"></a>執行 MethodCall 範例  

1.  將檔案 Input.xml 的複本貼到 In 資料夾。  

2.  觀察在 Out 資料夾中建立的 .xml 檔案。 此檔案包含要求的加法或減法計算的結果。 這個檔案的名稱的格式\< *MessageID*\>.xml，其中*\<MessageID\>* 會產生來唯一識別該訊息的 GUID.  

3.  您可修改輸入檔案，要求不同的加法或減法計算。  

## <a name="uninstalling-this-sample"></a>解除安裝這個範例  

#### <a name="to-uninstall-the-methodcall-sample"></a>解除安裝 MethodCall 範例  

1. 在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元，變更目錄 (**cd**) 來\<*範例路徑*\>\Orchestrations\MethodCall\\。  

2. 執行 Cleanup.bat。  

## <a name="see-also"></a>另請參閱  
 [協調流程 (BizTalk Server Samples 資料夾)](../core/orchestrations-biztalk-server-samples-folder.md)