---
title: "如何使用追蹤公用程式中主控件初始化的 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host initiated SSO, trace utility
- trace utility
ms.assetid: a53444d1-3f63-42a6-8ee6-b60ff9af9e41
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e00514515b31e79655fe457e1aa8682edf002183
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-trace-utility-in-host-initiated-sso"></a>如何使用追蹤公用程式中主控件初始化的 SSO
疑難排解的主要方法是追蹤。  
  
## <a name="tracing"></a>追蹤  
 使用「追蹤」命令列公用程式在 SSO 中啟用追蹤。  
  
> [!NOTE]
>  若要讓追蹤命令發揮效用，tracelog.exe 檔案必須位於下列目錄：  
>   
>  \<*磁碟機*>: Files\Enterprise Single Sign-on \Program Files\Common  
  
> [!NOTE]
>  您可以從下列位置下載這個檔案： [http://go.microsoft.com/fwlink/?LinkId=59534](http://go.microsoft.com/fwlink/?LinkId=59534)  
  
#### <a name="to-use-the-trace-utility"></a>使用追蹤公用程式  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**Trace – start – high**將追蹤層級設定為高，並開始追蹤。  
  
5.  執行主控件初始化的 SSO 的實例。  
  
6.  型別**Trace – 停止**以結束追蹤。 會在上述目錄中產生一個 .bin 檔案，您可以將該檔案傳送至 Microsoft 進行分析。  
  
## <a name="see-also"></a>另請參閱  
 [主控件初始化的 SSO](../core/host-initiated-sso.md)