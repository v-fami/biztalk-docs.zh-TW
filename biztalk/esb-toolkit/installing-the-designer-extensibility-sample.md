---
title: 安裝設計工具擴充性範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eba13a4a-1b87-4268-af91-29af3a5bc5ef
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7068f86f3e6be2cd71741a6afe5f2438ac3800b4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985711"
---
# <a name="installing-the-designer-extensibility-sample"></a>安裝設計工具擴充性範例
本章節描述的程序安裝設計工具擴充性範例。 您必須安裝中的範例[安裝和執行路線入口範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)並[安裝和執行動態解析範例](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)安裝和使用此範例之前。  

 **若要安裝的設計工具擴充性範例**  

1. 在 Windows 檔案總管中，開啟 資料夾 \Source\Samples\Designer Extensibility Samples\Extenders.Itinerary.OrchestrationSample，您的安裝位置[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再開啟 Microsoft Visual Studio 方案檔名為Extenders.Itinerary.OrchestrationSample.sln。  

2. 在 Visual Studio 中，按一下**建置方案**上**建置**功能表。  

3. 關閉 Visual Studio。  

4. 在 Windows 檔案總管中，開啟 資料夾 \Source\Samples\Designer Extensibility Samples\Extenders.Resolvers.ResolverSample，您的安裝位置[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再開啟 Visual Studio 方案檔名為Extenders.Resolvers.ResolverSample.sln。  

5. 在 Visual Studio 中，按一下**建置方案**上**建置**功能表。  

6. 關閉 Visual Studio。  

7. 在 Windows 檔案總管中，開啟路線設計工具安裝路徑下的 \Lib 資料夾。  

8. 從先前步驟中建置的 Visual Studio 方案的 \bin\Debug 資料夾，將檔案複製 Extenders.Resolvers.ResolverSample.dll 和 Extenders.Itinerary.OrchestrationSample.dll \Lib 目錄。
