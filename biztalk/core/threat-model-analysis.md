---
title: 威脅模型分析 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TMA, about TMA
- TMA
- TMA, procedure steps
ms.assetid: dfbf46aa-0a35-4925-8718-df8591efc279
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06f5de73434d2c3a7bf67e659c6566b530b38aeb
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22279910"
---
# <a name="threat-model-analysis"></a>威脅模型分析
威脅模型分析 (TMA) 是一種分析，可協助判斷對產品、應用程式或環境造成的安全性風險，以及攻擊會如何出現。 其目標是用以判斷哪些威脅需要防護以及如何減輕這些威脅。  
  
 本節提供 TMA 程序的概要資訊。 如需詳細資訊，請參閱第 4 章 *撰寫安全程式碼，第二版*, 、 Michael Howard 與 David LeBlanc。  
  
 TMA 的一些優點為：  
  
-   讓您對應用程式更加瞭解  
  
-   協助您尋找錯誤  
  
-   可協助新的小組成員詳細瞭解應用程式  
  
-   包含應用程式上建置的其他小組之重要資訊  
  
-   對測試人員相當有用  
  
 執行 TMA 的概要步驟：  
  
-   步驟 1： 收集背景資訊  
  
-   步驟 2： 建立和分析威脅模型  
  
-   步驟 3： 檢視威脅  
  
-   步驟 4： 識別防護技術  
  
-   步驟 5： 文件安全性模型和部署考量  
  
-   步驟 6： 實作和測試防護  
  
-   步驟 7： 保持威脅模型與設計同步  
  
## <a name="step-1-collect-background-information"></a>步驟 1： 收集背景資訊  
 為準備一個成功的 TMA，您必須收集一些背景資訊。 依照下列方式分析目標環境 (應用程式、程式或整個基礎結構) 是相當有用的：  
  
-   識別使用實例。 針對目標環境的每個使用實例，識別您預期公司如何使用目標環境，以及對目標環境的限制。 此資訊可協助定義威脅模型討論的範圍，並提供資產 (對您公司有價值的任何事物，例如資料與電腦) 與進入點的指標。  
  
-   為每個實例建立資料流程圖 (DFD)。 請確定您對威脅的瞭解夠深入。  
  
-   決定目標環境的界限與範圍。  
  
-   瞭解信任與不信任元件之間的界限。  
  
-   瞭解每個元件的組態與管理模型。  
  
-   建立外部相依性的清單。  
  
-   建立每個元件相依的其他元件之假設清單。 這可以協助與其他小組一起驗證跨元件假設、動作項目以及後續項目。  
  
## <a name="step-2-create-and-analyze-the-threat-model"></a>步驟 2： 建立和分析威脅模型  
 在您收集背景資訊之後，應該召開威脅模型會議。 請確定每個開發領域 (例如，程式管理人員、開發人員以及測試人員) 至少有一位成員出席會議。 請務必提醒與會人員，會議目的是要找出威脅，而不是修正威脅。 在威脅模型會議期間，執行下列動作：  
  
-   檢查每個使用實例的 DFD。 在每個使用實例識別下列項目：  
  
    -   進入點  
  
    -   信任界限  
  
    -   從輸入點到最後靜止位置的資料流 (然後返回)  
  
-   請注意相關的資產。  
  
-   討論每個 DFD，並尋找下列類別的 dfd 的所有項目中的威脅︰ **S**假冒識別， **T**ampering 資料， **R**否認， **我**資訊洩漏 **D**拒絕服務，以及 **E**提高權限。  
  
-   建立已識別威脅的清單。 我們建議此清單包含下列︰ 標題、 簡短描述 （包括威脅樹狀圖）、 資產、 影響、 風險、 防護技術、 防護狀態和錯誤數目。  
  
    > [!NOTE]
    >  您可以在檢視威脅時新增風險、防護技術以及防護狀態。 在威脅模型會議期間，請勿花費太多時間在這些領域。  
  
## <a name="step-3-review-threats"></a>步驟 3： 檢視威脅  
 在您識別對環境的威脅之後，必須將每個威脅的風險排名，並決定如何回應每個威脅。 您可以在其他小組會議或是透過電子郵件來執行此動作。 您可以使用下列影響類別來計算風險洩露︰ **D**損害的可能性、 **R**eproducibility， **E**xploitability， **A**受使用者和 **D**iscoverability。  
  
 在您擁有依照風險優先順序排列的目標環境之威脅清單後，必須決定將如何回應每個威脅。 您的回應可以是不做任何動作 (通常不是好選擇)、警告使用者可能的問題、移除問題或是修正問題。  
  
## <a name="step-4-identify-mitigation-techniques-and-technologies"></a>步驟 4： 識別防護技術  
 在您識別要修正的威脅之後，必須決定每個威脅的可用防護技術，以及最適當的技術以降低每個威脅的影響。  
  
 例如，視目標環境的詳細情況而定，您可以使用授權技術來降低資料竄改威脅的影響。 接著您必須決定要使用的適當授權技術 (例如，判別存取控制清單 (DACL)、權限或 IP 限制)。  
  
> [!IMPORTANT]
>  當您評估要使用的防護技術時，必須考量是否符合您公司的商務考量，以及是否有任何公司政策會影響要選擇的防護技術。  
  
 在完成 TMA 之後，執行下列動作：  
  
-   記錄安全性模型與部署考量  
  
-   實作和測試防護  
  
-   保持威脅模型與設計同步  
  
## <a name="step-5-document-security-model-and-deployment-considerations"></a>步驟 5： 文件安全性模型和部署考量  
 在 TMA 期間記錄所發現的狀況，並決定如何降低對目標環境威脅的影響，是非常有用的。 本文件對於品質保證 (QA)、測試、支援以及作業人員是非常有用的。 包含與目標環境互動和介入目標環境的其他應用程式之資訊，以及防火牆與拓樸建議和需求之資訊。  
  
## <a name="step-6-implement-and-test-mitigations"></a>步驟 6： 實作和測試防護  
 當您的小組準備修正在 TMA 期間識別的威脅時，請務必使用開發和部署檢查清單，以遵循安全準則和部署標準，協助將新威脅的產生降到最低。  
  
 在您實作防護之後，請務必測試防護，以確定它可提供針對威脅所需的防護層級。  
  
## <a name="step-7-keep-the-threat-model-in-sync-with-design"></a>步驟 7： 保持威脅模型與設計同步  
 當您新增應用程式、伺服器以及其他項目至環境中時，請務必重新瀏覽威脅模型分析的發現，並針對任何新功能執行 TMA。  
  
## <a name="see-also"></a>另請參閱  
[小型至中型公司的安全性案例研究](../core/security-case-studies-for-small-to-medium-sized-companies.md)   
 [威脅模型分析的範例案例](../core/sample-scenarios-for-threat-model-analysis.md)