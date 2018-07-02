---
title: 產生 WSDL 與 WCF LOB 配接器 SDK |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f701d78d-b3ad-4f75-b814-e5b1f1319fb9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eaf5ed992864c11d360baa30f35983f0082213b3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971071"
---
# <a name="generate-wsdl-with-the-wcf-lob-adapter-sdk"></a>產生 WSDL 與 WCF LOB 配接器 SDK
在開發配接器，或從 LOB 系統變更傳回的中繼資料，通常很有用，檢視 Web 服務描述語言 (WSDL) 所傳回的介面卡，以確認您的作業的中繼資料，會產生期間正確。 有數種方法來產生的 WSDL。 本主題提供使用 svcutil.exe，並瀏覽中繼資料搜尋控制項的相關資訊。  

  
## <a name="use-svcutilexe"></a>使用 svcutil.exe  
 Svcutil.exe 會是命令列公用程式隨附於 Windows SDK 的 URL 和選擇性參數，會接受及傳回 WSDL。 使用 svcutil.exe 傳回的 WSDL Echo 配接器的範例如下：  
  
 ```
 Svcutil.exe “echov2://lobhostname/lobapplication?enableAuthentication=False” /target:metadata
 ```
  
 這會將中繼資料儲存 Microsoft.Adapters.Samples.Echov2.wsdl。 如果您的配接器有許多作業，您可以選擇使用以傳回所需的作業 ' op = OperationName' 做為 URI 的一部分。 使用此傳回 EchoStrings 資訊的範例如下：  
  
```  
SvcUtil.exe “echov2://lobhostname/lobapplication?enableAuthentication=False&op=Echo/EchoStrings” /target:metadata  
```  
  
## <a name="use-the-metadata-search-browse-control"></a>使用中繼資料搜尋瀏覽控制項  
 瀏覽中繼資料搜尋控制項是 Windows 控制項中所包含的精靈中使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 您可以將此控制項加入任何 Windows Form 專案在 Visual Studio 中，和使用它來選取您的配接器所需的作業，然後產生的 WSDL。  
  
1. 開啟[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]命令提示字元。  
  
2. 在上**檔案**功能表上，選取**新增**，然後按一下**專案**。  
  
3. 在 **新的專案**對話方塊中，選取**Windows 應用程式**從**範本**。 輸入專案名稱，然後按一下**確定**。  
  
4. 開啟**工具箱**，展開**通用控制項**，以滑鼠右鍵按一下**工具箱**，然後按一下**選擇項目**。  
  
5. 在 [**選擇工具箱項目**] 對話方塊中，尋找**MetadataUserControl**上 **.NET Framework 元件**索引標籤上，選取此項目，旁邊的核取方塊，然後按一下**確定**。  
  
6. 從 [工具箱] 拖曳到 Form1 的 MetadataUserControl。 您可能需要調整表單以查看整個控制項的大小。 您應該能夠立即執行專案，並確認控制項正常運作，可讓您選取的配接器和作業。  
  
7. 使用這個控制項產生的 WSDL，您必須將程式碼加入您的表單來呼叫**GetWsdl**此控制項的方法。 下列範例示範如何呼叫**GetWsdl**並將資料儲存至檔案：  
  
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