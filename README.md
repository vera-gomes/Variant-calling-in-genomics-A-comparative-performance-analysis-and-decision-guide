# Variant-calling-in-genomics-A-comparative-performance-analysis-and-decision-guide
<div align="center">

<h3>🧬 Final Table — Command Lines and Versions</h3>

<table>
  <thead>
    <tr>
      <th>Tool</th>
      <th>Version</th>
      <th>Command Line / Notes</th>
      <th>Citation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>GATK</b></td>
      <td>v4.4.0.0</td>
      <td><code>gatk HaplotypeCaller -R hg38.fa -I NA12878.bam -O GATK.vcf.gz --native-pair-hmm-threads 12</code></td>
      <td>McKenna et al., 2010</td>
    </tr>
    <tr>
      <td><b>FreeBayes</b></td>
      <td>v1.3.6</td>
      <td><code>freebayes -f hg38.fa NA12878.bam &gt; FreeBayes.vcf</code></td>
      <td>Garrison &amp; Marth, 2012</td>
    </tr>
    <tr>
      <td><b>SAMtools</b></td>
      <td>v1.19</td>
      <td><code>samtools mpileup -uf hg38.fa NA12878.bam | bcftools call -mv -Ob -o Samtools.bcf</code><br><code>bcftools view Samtools.bcf &gt; Samtools.vcf</code></td>
      <td>Li et al., 2009</td>
    </tr>
    <tr>
      <td><b>BCFtools</b></td>
      <td>v1.19</td>
      <td><i>Used jointly with SAMtools for variant calling and VCF conversion</i></td>
      <td>Danecek et al., 2021</td>
    </tr>
    <tr>
      <td><b>Strelka2</b></td>
      <td>v2.9.10</td>
      <td><code>configureStrelkaGermlineWorkflow.py --bam NA12878.bam --referenceFasta hg38.fa --runDir strelka_run</code><br><code>cd strelka_run &amp;&amp; ./runWorkflow.py -m local -j 12</code></td>
      <td>Kim et al., 2018</td>
    </tr>
    <tr>
      <td><b>DeepVariant</b></td>
      <td>v1.6.0 (TensorFlow 2.11)</td>
      <td><code>/opt/deepvariant/bin/run_deepvariant --model_type=WGS --ref=hg38.fa --reads=NA12878.bam --output_vcf=DeepVariant.vcf.gz --num_shards=12</code><br><i>Illumina WGS pre-trained model</i></td>
      <td>Poplin et al., 2018</td>
    </tr>
    <tr>
      <td><b>Octopus</b></td>
      <td>v1.10.0</td>
      <td><code>octopus -R hg38.fa -I NA12878.bam -o Octopus.vcf.gz --threads 12 --target-somatic-calls false</code></td>
      <td>Cooke et al., 2021</td>
    </tr>
    <tr>
      <td><b>VarScan2</b></td>
      <td>v2.4.6</td>
      <td><code>samtools mpileup -B -f hg38.fa NA12878.bam &gt; NA12878.pileup</code><br><code>java -jar VarScan.v2.4.6.jar mpileup2snp NA12878.pileup --output-vcf 1 &gt; Varscan2.vcf</code></td>
      <td>Koboldt et al., 2012</td>
    </tr>
  </tbody>
</table>

<p><i>Environment:</i> Ubuntu 22.04 LTS · 12-core Intel Xeon E5-2670 · 16 GB RAM · Reference: GRCh38 (hg38) · Truth set: GIAB NA12878 (HG001)</p>

</div>
