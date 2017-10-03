---
title: "檢查清單： 匯出繫結到另一個應用程式從 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 152924e6-da64-4db9-a852-bdb4e79687fb
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df60a6fd1b266403a5c43b5f76bf7594cad4f41a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-exporting-bindings-from-one-application-to-another"></a>檢查清單： 從另一個應用程式匯出繫結
本主題描述傳送至另一個應用程式開發或實際執行環境中的一個應用程式的繫結所需的步驟。 此程序會使用.msi 檔案將應用程式部署程序類似。 不過，當您部署使用的.msi 檔案的應用程式時，處理程序會自動建立應用程式。 當您從應用程式之間傳輸的繫結時，相反地，必須已存在目的端應用程式。  
  
|步驟|參考|  
|-----------|---------------|  
|確定您有適當的權限來執行匯出作業。|[管理應用程式的權限](../technical-guides/permissions-for-managing-an-application.md)|  
|建立匯入應用程式繫結到目的地應用程式。|-   [建立應用程式](../technical-guides/creating-an-application.md)<br />-< 建立 BizTalk 應用程式 > 一節[部署應用程式的最佳作法](../technical-guides/best-practices-for-deploying-an-application.md)|  
|匯出到繫結檔案的來源應用程式的繫結。|-   [如何匯出繫結至繫結檔案](../technical-guides/how-to-export-bindings-to-a-binding-file.md)<br />-「 匯出 BizTalk 應用程式 」 一節[部署應用程式的最佳作法](../technical-guides/best-practices-for-deploying-an-application.md)<br />-「 匯出 BizTalk 應用程式 」 一節[與部署應用程式的已知問題](../technical-guides/known-issues-with-deploying-an-application.md)。|  
|繫結檔案中的將繫結匯入到目的地應用程式。|-   [如何從繫結檔案匯入繫結](../technical-guides/how-to-import-bindings-from-a-binding-file.md)<br />-「 匯入 BizTalk 應用程式 」 一節[部署應用程式的最佳作法](../technical-guides/best-practices-for-deploying-an-application.md)<br />-「 匯入 BizTalk 應用程式 」 一節[與部署應用程式的已知問題](../technical-guides/known-issues-with-deploying-an-application.md)。|