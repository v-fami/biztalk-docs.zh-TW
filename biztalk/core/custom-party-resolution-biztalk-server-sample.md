---
title: 自訂合作對象解析 （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, parties
- pipeline components [custom], examples
- pipeline components [custom], parties
- examples, pipeline components [custom]
- parties, pipeline components [custom]
- parties, custom
ms.assetid: 1f88450f-5fe9-486d-bfb8-fd11181c78b4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7b88d8126a1d63760888edbcd7691ad4bd76426
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238694"
---
# <a name="custom-party-resolution-biztalk-server-sample"></a>自訂合作對象解析 （BizTalk Server 範例）
此「自訂合作對象解析」範例示範如何解析自訂合作對象。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 「自訂合作對象解析」範例使用下列步驟完成其工作：  
  
1.  從資料夾擷取 XML 文件。  
  
2.  管線會解析合作對象。  
  
3.  將 XML 訊息寫入資料夾中。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑 >* \Pipelines\CustomPartyResolution\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|AssemblyInfo.cs|組件資訊 C# 原始程式檔。|  
|Cleanup.bat|清除批次檔。|  
|CustomPartyResolution.sln|解決方案檔案。|  
|CustomPartyResolutionBinding.xml|繫結檔案。|  
|CustomPartyResolutionPipeline.btp|管線檔案。|  
|CustomPartyResolutionPipeline.btproj|管線專案檔。|  
|CustomPartyResolutionPipelineComponent.cs|管線元件 C# 原始程式碼。|  
|CustomPartyResolutionPipelineComponent.csproj|管線元件 Visual Studio 專案檔。|  
|InboundDocumentSchema.xsd|輸入文件結構描述。|  
|PartyResolutionStream.cs|合作對象解析資料流 C# 原始程式碼。|  
|RoutingPropertySchema.xsd|路由屬性結構描述檔。|  
|SampleInboundDocumentSchema.xml|輸入文件結構描述檔。|  
|SampleInboundDocumentSchema_Party1.xml|範例資料執行個體。|  
|SampleInboundDocumentSchema_Party2.xml|範例資料執行個體。|  
|Setup.bat|建置和安裝範例管線元件批次檔。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
  
#### <a name="to-build-and-initialize-the-custom-party-resolution-sample"></a>若要建置和初始化自訂合作對象解析範例  
  
1.  在命令視窗中，將目錄變更 (**cd**) 至下列資料夾：  
  
     *\<範例路徑 >* \Pipelines\CustomPartyResolution\  
  
2.  執行 Setup.bat 檔案，這會執行下列動作：  
  
    -   建立在範例中使用的輸入和輸出目錄。  
  
    -   產生新的金鑰檔案。  
  
    -   建置及部署「自訂合作對象解析」管線元件。  
  
    -   若要建置的管線元件會將複製*\<安裝路徑 >* \Pipeline Components 目錄。  
  
    -   建立傳送埠和接收埠。  
  
> [!NOTE]
>  在嘗試執行此範例之前，您應該確認在建置和初始化程序期間沒有報告錯誤。  
  
## <a name="running-this-sample"></a>執行此範例  
  
#### <a name="to-run-the-custom-party-resolution-sample"></a>若要執行自訂合作對象解析範例  
  
1.  將 SampleInboundDocumentSchema_Party1.xml 或 SampleInboundDocumentSchema_Party2.xml 檔案複製到 \In 資料夾。  
  
2.  結果會出現在 \Out 資料夾與檔案名稱*guid*.xml。  
  
## <a name="see-also"></a>另請參閱  
 [管線 （BizTalk Server 範例資料夾）](../core/pipelines-biztalk-server-samples-folder.md)