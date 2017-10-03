---
title: "偵錯自訂管線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27e5445a-6415-4c52-a450-b74a71fc4aa2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a0f701518714aaf28d0ae07867c8c490c140fa0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="debugging-custom-pipelines"></a>偵錯自訂管線
當自訂管線中發生訊息處理失敗時，您可以使用來源層級偵錯來識別和修正問題。 使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 偵錯工具可以執行來源層級偵錯，其方式是將此工具附加到 BTSNTSVC.exe (如果自訂管線已部署) 或 Pipeline.exe (如果使用獨立管線工具)。  
  
## <a name="procedures"></a>程序  
 您可以使用下列程序來偵錯自訂管線。  
  
### <a name="how-to-debug-a-deployed-pipeline"></a>如何偵錯已部署的管線  
 追蹤查詢，從 [群組中樞] 頁面中和事件檢視器，提供有關訊息處理已部署的元件中失敗的有用資訊。 這項資訊通常可用來縮小問題。 一旦斷定是自訂管線的關係，就可以使用來源層級偵錯找出任何有問題的程式碼。  
  
##### <a name="to-debug-a-deployed-custom-pipeline-using-visual-studio"></a>若要部署自訂管線，使用 Visual Studio 偵錯  
  
1.  將自訂管線專案方案載入至 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
2.  變更您的方案的輸出路徑*\<安裝資料夾 >*\Pipeline Components。 在方案總管 中，以滑鼠右鍵按一下您的專案，按一下 建置 索引標籤，然後依序按一下以變更輸出路徑**瀏覽**按鈕，選取*\<安裝資料夾 >*\管線元件目錄。  
  
3.  從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，按一下 部署方案**建置**&#124;**部署**。  
  
4.  重新啟動執行管線的主控件執行個體。 使用 BizTalk Server 管理主控台，瀏覽至執行管線的主控件執行個體，請以滑鼠右鍵按一下主控件執行個體然後按一下 **重新啟動**。  
  
5.  附加[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BTSNTSVC.exe 偵錯工具。 這可藉由按一下**偵錯**&#124;**附加至處理序**、 顯示處理程序在所有工作階段，然後再連按兩下 BTSNTSVC.exe。  
  
6.  設定中斷點。  
  
7.  將訊息拖放到適當的位置，以起始自訂管線元件。 處理應該會在您設定的中斷點上停下來。  
  
> [!NOTE]
>  如果程式碼擲回例外狀況，BizTalk Server 將會加以攔截，最終則擱置該訊息。 為了避免這種情況，您應該在最有可能發生的例外狀況上中斷。  
  
### <a name="how-to-debug-using-pipelineexe"></a>如何使用 Pipeline.exe 進行偵錯  
 您也可以測試使用 Pipeline.exe 的自訂管線。 這樣的優點是不需要您部署的管線，但會犧牲類似實際執行環境的狀況下執行。  
  
> [!NOTE]
>  如果自訂管線使用一般檔案組合器/解譯器，則 Pipeline.exe 將無法正確執行。 這是因為 Pipeline.exe 不會存取 BizTalk 資料庫。 其中一個解決方案是移除組合器 / 解譯器元件，並使用 FFDasm.exe 和 FFAsm.exe 個別加以測試。 請參閱[管線工具](../core/pipeline-tools.md)如需詳細資訊。  
  
##### <a name="to-debug-a-custom-pipeline-using-pipelineexe-and-visual-studio"></a>若要偵錯自訂管線中使用 Pipeline.exe 和 Visual Studio  
  
1.  將自訂管線專案方案載入至 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
2.  變更您的方案的輸出路徑*\<安裝資料夾 >*\Pipeline Components。 在方案總管 中，以滑鼠右鍵按一下您的專案，按一下 建置 索引標籤，然後依序按一下以變更輸出路徑**瀏覽**按鈕，選取*\<安裝資料夾 >*\管線元件目錄。  
  
3.  變更方案的起始動作。 在 方案總管 中，以滑鼠右鍵按一下您的專案，按一下 偵錯 索引標籤，按一下 啟動外部程式，然後按一下**...** 瀏覽至*\<安裝資料夾 >*\SDK\Utilities\PipelineTools 並選擇 Pipeline.exe。 在啟動選項 下輸入的命令列引數適用於您的元件。 如需 Pipeline.exe 的詳細資訊，請參閱[管線工具](../core/pipeline-tools.md)。 指定管線和範例檔案的一般組態設定：  
  
    ```  
    <Path>\YourPipeline.btp -d <Path>\YourTestFile.txt -c  
    ```  
  
4.  設定您的中斷點。  
  
5.  按 F5 開始偵錯。  
  
## <a name="see-also"></a>另請參閱  
 [管線工具](../core/pipeline-tools.md)