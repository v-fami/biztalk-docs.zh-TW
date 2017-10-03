---
title: "產生 WSDL 與 WCF LOB 配接器 SDK |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f701d78d-b3ad-4f75-b814-e5b1f1319fb9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1075bbe59e15e3eeabde6c1d5c954460d1cb570
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="generate-wsdl-with-the-wcf-lob-adapter-sdk"></a>產生 WSDL 與 WCF LOB 配接器 SDK
在開發配接器，或從 LOB 系統變更傳回的中繼資料，通常會很有用，檢視 Web 服務描述語言 (WSDL) 所傳回的介面卡以確認您的作業的中繼資料，會產生期間正確。 有數種方法來產生的 WSDL。 本主題提供使用 svcutil.exe，並瀏覽中繼資料搜尋控制項的相關資訊。  

  
## <a name="use-svcutilexe"></a>使用 svcutil.exe  
 Svcutil.exe 會隨附於 Windows SDK，可接受的 URL 和選擇性參數，並傳回 WSDL 的命令列公用程式。 使用 svcutil.exe 傳回 WSDL 回應配接器的範例如下：  
  
 ```
 Svcutil.exe “echov2://lobhostname/lobapplication?enableAuthentication=False” /target:metadata
 ```
  
 這是為 Microsoft.Adapters.Samples.Echov2.wsdl 儲存的中繼資料。 如果您的配接器有許多作業，您可以選擇所需的作業使用傳回的 ' op = OperationName' 做為 URI 的一部分。 使用此傳回 EchoStrings 資訊的範例如下：  
  
```  
SvcUtil.exe “echov2://lobhostname/lobapplication?enableAuthentication=False&op=Echo/EchoStrings” /target:metadata  
```  
  
## <a name="use-the-metadata-search-browse-control"></a>使用搜尋中繼資料瀏覽控制項  
 中繼資料瀏覽搜尋控制項是使用包含在精靈中的 Windows 控制項[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 您可以將此控制項加入任何 Windows Form 專案在 Visual Studio 中，和使用它來選取您的配接器所需的操作，然後產生的 WSDL。  
  
1.  開啟[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]命令提示字元。  
  
2.  在**檔案**功能表上，選取**新增**，然後按一下 **專案**。  
  
3.  在**新專案**對話方塊中，選取**Windows 應用程式**從**範本**。 輸入專案名稱，然後再按一下**確定**。  
  
4.  開啟**工具箱**，依序展開**通用控制項**，以滑鼠右鍵按一下**工具箱**，然後按一下 **選擇項目**。  
  
5.  在**選擇工具箱項目**對話方塊中，尋找**MetadataUserControl**上**.NET Framework 元件**索引標籤上，選取此項目，旁邊的核取方塊，然後按一下  **確定**。  
  
6.  從 [工具箱] 將 MetadataUserControl 拖曳至 Form1。 您可能需要調整表單，以查看整個控制項的大小。 您應該能夠立即執行專案，並確認控制項的功能，可讓您選取配接器和作業。  
  
7.  若要使用這個控制項產生 WSDL，您必須將程式碼加入至表單呼叫**GetWsdl**這個控制項的方法。 下列範例示範如何呼叫**GetWsdl**並將資料儲存至檔案：  
  
    ```csharp  
    private void button1_Click(object sender, EventArgs e)  
    {  
       ServiceDescription sd = mdUserControl.GetWsdl();  
       FileStream myFileStream = new FileStream(tbWsdlFileName.Text, FileMode.OpenOrCreate, FileAccess.Write);  
       StreamWriter myStreamWriter = new StreamWriter(myFileStream);  
       sd.Write(myStreamWriter);  
       myStreamWriter.Flush();  
       myStreamWriter.Close();  
       MessageBox.Show("WSDL file " + tbWsdlFileName.Text + " is created.");  
    }  
  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF LOB 配接器 SDK 所建立的配接器進行疑難排解](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md)