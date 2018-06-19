---
title: 配接器 WSDL 檔案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4b35c0-1e4b-4106-8921-29d14f976d65
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c600729411066637e021a118b88ec97ffd3b25fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22229822"
---
# <a name="adapter-wsdl-files"></a><span data-ttu-id="5a612-102">配接器 WSDL 檔案</span><span class="sxs-lookup"><span data-stu-id="5a612-102">Adapter WSDL Files</span></span>
<span data-ttu-id="5a612-103">在 新增配接器中繼資料精靈 Web 服務描述語言 (WSDL) 檔案會選取並將其輸入**選取要匯入服務**頁面。</span><span class="sxs-lookup"><span data-stu-id="5a612-103">In the Add Adapter Metadata Wizard the Web Services Description Language (WSDL) file is selected and input on the **Select Services to Import** page.</span></span> <span data-ttu-id="5a612-104">該精靈會讀取由服務公開並由使用者選取的 WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="5a612-104">The wizard reads the WSDL files exposed by the service and selected by the user.</span></span> <span data-ttu-id="5a612-105">然後便會在 BizTalk 專案中建立並新增一個 XSD 檔案，以及一個協調流程。</span><span class="sxs-lookup"><span data-stu-id="5a612-105">It then creates and adds an XSD file and an orchestration in the BizTalk project.</span></span>  
  
 <span data-ttu-id="5a612-106">在範例 FILE 配接器中，Service1.wsdl 檔案包含 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 新增至專案的 XSD 定義。</span><span class="sxs-lookup"><span data-stu-id="5a612-106">In the sample file adapter, the Service1.wsdl file contains the XSD definitions that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adds to the project.</span></span> <span data-ttu-id="5a612-107">您可以選擇修改 Service1.wsdl 檔案，或是建立您自己的 WSDL 檔案 (其中包含新增至 BizTalk 專案的 XSD 定義)。</span><span class="sxs-lookup"><span data-stu-id="5a612-107">You may choose to modify the Service1.wsdl file or create your own WSDL file that contains the XSD definitions to add to your BizTalk project.</span></span>  
  
 <span data-ttu-id="5a612-108">下列程式碼來自於 Service1.wsdl 檔案：</span><span class="sxs-lookup"><span data-stu-id="5a612-108">The following code is from the Service1.wsdl file:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<definitions xmlns:http="http://schemas.xmlsoap.org/wsdl/http/" xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/" xmlns:s="http://www.w3.org/2001/XMLSchema" xmlns:s0="http://tempuri.org/" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/" xmlns:tm="http://microsoft.com/wsdl/mime/textMatching/" xmlns:mime="http://schemas.xmlsoap.org/wsdl/mime/" targetNamespace="http://tempuri.org/" xmlns="http://schemas.xmlsoap.org/wsdl/">  
  <types>  
    <s:schema elementFormDefault="qualified" targetNamespace="http://tempuri.org/">  
      <s:element name="GetTaxID">  
        <s:complexType />  
      </s:element>  
      <s:element name="GetTaxIDResponse">  
        <s:complexType>  
          <s:sequence>  
            <s:element minOccurs="0" maxOccurs="1" name="GetTaxIDResult" type="s:string" />  
          </s:sequence>  
        </s:complexType>  
      </s:element>  
      <s:element name="GetPayStub">  
        <s:complexType />  
      </s:element>  
      <s:element name="GetPayStubResponse">  
        <s:complexType>  
          <s:sequence>  
            <s:element minOccurs="0" maxOccurs="1" name="GetPayStubResult" type="s:string" />  
          </s:sequence>  
        </s:complexType>  
      </s:element>  
      <s:element name="GetTaxInfo">  
        <s:complexType />  
      </s:element>  
  
```